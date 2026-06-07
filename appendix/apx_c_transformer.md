# 附录C：从零实现一个Transformer

用PyTorch实现Transformer编码器的核心组件。这不是完整的生产代码，而是帮助理解每个部分在做什么。

## 自注意力

`python
import torch
import torch.nn as nn
import torch.nn.functional as F

class SelfAttention(nn.Module):
    def __init__(self, d_model, n_heads):
        super().__init__()
        self.d_k = d_model // n_heads
        self.n_heads = n_heads
        self.W_q = nn.Linear(d_model, d_model)
        self.W_k = nn.Linear(d_model, d_model)
        self.W_v = nn.Linear(d_model, d_model)
        self.W_o = nn.Linear(d_model, d_model)

    def forward(self, x, mask=None):
        B, T, C = x.shape
        # Project to Q, K, V and split into heads
        q = self.W_q(x).view(B, T, self.n_heads, self.d_k).transpose(1, 2)
        k = self.W_k(x).view(B, T, self.n_heads, self.d_k).transpose(1, 2)
        v = self.W_v(x).view(B, T, self.n_heads, self.d_k).transpose(1, 2)
        # Scaled dot-product attention
        scores = (q @ k.transpose(-2, -1)) / (self.d_k ** 0.5)
        if mask is not None:
            scores = scores.masked_fill(mask == 0, float('-inf'))
        attn = F.softmax(scores, dim=-1)
        # Apply attention to values
        out = (attn @ v).transpose(1, 2).contiguous().view(B, T, C)
        return self.W_o(out)
`

## Transformer编码器层

`python
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
        # Self-attention + residual + layernorm
        x = x + self.drop(self.attn(self.ln1(x), mask))
        # Feed-forward + residual + layernorm
        x = x + self.drop(self.ff(self.ln2(x)))
        return x
`

## 关键观察

1. SelfAttention中，QKV投影后分成多个头，每个头独立计算注意力，最后拼接
2. scores/ sqrt(d_k) 是缩放因子，防止softmax饱和
3. mask用于解码器中阻止看到未来位置
4. TransformerBlock中两次残差连接+LayerNorm（Pre-LN形式）
5. FFN先升维（d_model→d_ff）再降维（d_ff→d_model），GELU激活
