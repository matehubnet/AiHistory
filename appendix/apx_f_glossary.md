# 附录F：术语表

**AGI (Artificial General Intelligence)** 通用人工智能，能在所有认知任务上匹敌或超越人类。

**Attention** 注意力机制，让模型动态选择关注输入的哪些部分。核心公式：softmax(QK^T/sqrt(dk))*V。

**Backpropagation** 反向传播，用链式法则计算多层网络中每个权重的梯度。

**BERT** Google的双向预训练语言模型，用掩码语言模型做预训练。

**CNN** 卷积神经网络，用卷积核提取局部特征，适合图像处理。

**CoT (Chain-of-Thought)** 思维链，让模型先展示推理过程再给答案。

**Diffusion Model** 扩散模型，从噪声逐步去噪生成数据，训练稳定可控。

**Dropout** 训练时随机关闭神经元，防止过拟合。

**ELIZA Effect** 人类倾向于对表现出对话行为的系统归因智能。

**Embedding** 嵌入，把离散符号（词、物品）映射到连续向量空间。

**Fine-tuning** 微调，在预训练模型上用特定任务数据继续训练。

**GAN** 生成对抗网络，生成器与判别器对抗训练。

**Gradient Descent** 梯度下降，沿负梯度方向更新权重以减小损失。

**Gradient Vanishing** 梯度消失，深层网络中梯度指数衰减导致靠近输入的层学不动。

**In-context Learning** 上下文学习，不修改参数只在输入中给例子就能学会新任务。

**KL Divergence** KL散度，衡量两个概率分布的差异。

**LLM** 大语言模型，参数量巨大的Transformer语言模型。

**LoRA** 低秩适配，只训练极少量参数的微调方法。

**Loss Function** 损失函数，衡量模型预测与真实值的差距。

**MoE** 混合专家模型，只激活部分专家减少计算量。

**MCP** Model Context Protocol，Anthropic发布的AI工具调用开放标准。

**Overfitting** 过拟合，模型在训练数据上表现好但在新数据上表现差。

**Perceptron** 感知机，最早的神经网络学习算法，只能处理线性可分问题。

**RAG** 检索增强生成，推理前先从外部数据库检索信息注入上下文。

**ReLU** 修正线性单元 f(z)=max(0,z)，解决sigmoid梯度消失。

**Residual Connection** 残差连接/跳跃连接，让梯度直通，解决深层网络退化问题。

**RLHF** 用人类反馈的强化学习，训练模型符合人类偏好。

**RNN** 循环神经网络，用隐藏状态处理变长序列。

**Scaling Laws** 规模法则，Loss与参数量/数据量/算力呈幂律关系。

**Self-Attention** 自注意力，序列中每个位置直接关注所有其他位置。

**Softmax** 把向量归一化为概率分布。

**SVM** 支持向量机，最大间隔分类器+核技巧。

**Test-time Compute** 推理时计算，推理时投入更多计算换更好的答案。

**Token** 语言模型处理的最小文本单位（词或子词）。

**Transformer** 基于自注意力的架构，当前所有大模型的基础。

**World Model** 世界模型，构建对环境的内部表示以预测和规划。
