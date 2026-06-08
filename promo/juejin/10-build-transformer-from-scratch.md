# 从零手写Transformer：用代码理解自注意力的每一个细节

> 本文改编自开源书籍《[AI简史：从感知机到大模型](https://github.com/matehubnet/AiHistory)》附录C。书中附录B还包含从零手写神经网络（NumPy反向传播）的完整实现。

---

理解Transformer最好的方式是手写一遍。不是复制粘贴，而是真正理解每一行在做什么。

让我们从最核心的自注意力开始，逐步构建一个完整的Transformer编码器。

## 第一步：自注意力——Transformer的灵魂

自注意力的计算只有4行核心代码：

```python
# 输入 x: (batch, seq_len, d_model)
q = W_q(x)  # 投影到Query空间
k = W_k(x)  # 投影到Key空间
v = W_v(x)  # 投影到Value空间
out = softmax(q @ k.T / sqrt(d_k)) @ v  # 注意力加权
```

逐行解析：

**q @ k.T** → 计算注意力得分矩阵。q[i] @ k[j] 表示位置i对位置j的"兴趣程度"。结果是一个 seq_len × seq_len 的矩阵。

**/ sqrt(d_k)** → 缩放因子。当维度d_k很大时，点积的值也很大，softmax会进入梯度极小的饱和区。除以sqrt(d_k)保持梯度稳定。

**softmax** → 归一化为概率分布。每个位置的注意力权重之和为1。

**@ v** → 用注意力权重对Value做加权平均。位置i的输出 = Σ(注意力权重[i,j] × V[j])。

## 第二步：多头注意力——同时学习多种关联

一个注意力头学一种关联模式。但语言中的关联是多样的：语法关系、指代关系、语义关系。

多头注意力的做法：把d_model维度切分成n_heads个头，每个头独立计算注意力，然后拼接。

```python
class SelfAttention(nn.Module):
    def __init__(self, d_model, n_heads):
        super().__init__()
        self.d_k = d_model // n_heads  # 每个头的维度
        self.n_heads = n_heads
        self.W_q = nn.Linear(d_model, d_model)
        self.W_k = nn.Linear(d_model, d_model)
        self.W_v = nn.Linear(d_model, d_model)
        self.W_o = nn.Linear(d_model, d_model)

    def forward(self, x, mask=None):
        B, T, C = x.shape
        # 投影到QKV，然后分成多个头
        q = self.W_q(x).view(B, T, self.n_heads, self.d_k).transpose(1, 2)
        k = self.W_k(x).view(B, T, self.n_heads, self.d_k).transpose(1, 2)
        v = self.W_v(x).view(B, T, self.n_heads, self.d_k).transpose(1, 2)
        # 缩放点积注意力
        scores = (q @ k.transpose(-2, -1)) / (self.d_k ** 0.5)
        if mask is not None:
            scores = scores.masked_fill(mask == 0, float('-inf'))
        attn = F.softmax(scores, dim=-1)
        # 加权平均后拼回头
        out = (attn @ v).transpose(1, 2).contiguous().view(B, T, C)
        return self.W_o(out)
```

关键细节：
- `view(B, T, n_heads, d_k).transpose(1, 2)` 把 (B, T, d_model) 变成 (B, n_heads, T, d_k)，让每个头独立处理
- 最后 `.contiguous().view(B, T, C)` 把所有头的输出拼接回 d_model 维度
- W_o 是输出的线性变换，融合不同头的信息

## 第三步：Transformer Block——残差+LayerNorm+FFN

一个完整的Transformer Block = 自注意力 + 前馈网络 + 两个残差连接 + 两个LayerNorm。

```python
class TransformerBlock(nn.Module):
    def __init__(self, d_model, n_heads, d_ff, dropout=0.1):
        super().__init__()
        self.attn = SelfAttention(d_model, n_heads)
        self.ln1 = nn.LayerNorm(d_model)
        self.ln2 = nn.LayerNorm(d_model)
        self.ff = nn.Sequential(
            nn.Linear(d_model, d_ff),
            nn.GELU(),
            nn.Linear(d_ff, d_model),
        )
        self.drop = nn.Dropout(dropout)

    def forward(self, x, mask=None):
        # 自注意力 + 残差 + LayerNorm
        x = x + self.drop(self.attn(self.ln1(x), mask))
        # 前馈 + 残差 + LayerNorm
        x = x + self.drop(self.ff(self.ln2(x)))
        return x
```

5个关键观察：

1. **Pre-LN vs Post-LN**：这里用的是Pre-LN（先LayerNorm再注意力），这是GPT-2之后的主流做法。原始Transformer用的是Post-LN，训练不稳定。

2. **残差连接**：`x = x + ...` 让梯度可以直通，避免梯度消失。这也是ResNet的核心思想。

3. **FFN的升维-降维**：d_model → d_ff → d_model。通常d_ff = 4 × d_model。先升维让模型在高维空间做非线性变换，再降维回来。GELU激活比ReLU更平滑。

4. **Dropout**：训练时随机丢弃部分输出，防止过拟合。推理时关闭。

5. **mask参数**：解码器中用来阻止看到未来位置——每个位置只能关注它之前的位置。

## 为什么这些设计选择很重要？

每一个看似微小的设计选择都有深层原因：

- **缩放因子 / sqrt(d_k)**：没有它，d_k=64时点积的方差是64，softmax输入值的范围是[-8, 8]，梯度几乎为零。有了缩放，方差回到1，softmax梯度正常。
- **多头而非单头**：实验证明单头注意力的模型效果明显差。不同头学到了不同的关联模式（注意力可视化可以验证）。
- **Pre-LN而非Post-LN**：Post-LN在训练初期残差路径上的LayerNorm会让输出偏移，导致梯度不稳定。Pre-LN先归一化再计算，梯度更稳定。
- **残差连接**：没有它，6层Transformer就很难训练。有了它，100+层也能训练（虽然100层Transformer不常见）。

## 完整实现

完整的Transformer实现（包括位置编码、编码器栈、解码器、分类头）见书中的附录C——用PyTorch逐行解析，包含可运行的完整代码。

附录B还有用NumPy从零实现反向传播的完整代码——不依赖任何框架，纯手写梯度计算。

---

> 本文是《AI简史》连载系列第10篇（完结篇）。
>
> 📖 完整内容见：[github.com/matehubnet/AiHistory](https://github.com/matehubnet/AiHistory)
>
> 🔥 21章正文 + 6个附录，从1943年M-P神经元到2026年世界模型：
> - 第1-3章：萌芽——符号与规则的时代
> - 第4-6章：数据与统计的时代
> - 第7-10章：深度学习的爆发
> - 第11-14章：Transformer与大模型时代
> - 第15-18章：大模型爆发与AGI之路
> - 第19-21章：展望——通向何方
>
> ⭐ 如果觉得有帮助，欢迎Star支持！
