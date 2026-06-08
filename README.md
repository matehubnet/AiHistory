# AI简史：从感知机到大模型
# AI History: From Perceptron to Large Language Models

[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)
[![GitHub stars](https://img.shields.io/github/stars/matehubnet/AiHistory.svg?style=social)](https://github.com/matehubnet/AiHistory/stargazers)
[![GitHub forks](https://img.shields.io/github/forks/matehubnet/AiHistory.svg?style=social)](https://github.com/matehubnet/AiHistory/network/members)
[![GitHub issues](https://img.shields.io/github/issues/matehubnet/AiHistory.svg)](https://github.com/matehubnet/AiHistory/issues)

**一本写给技术人的AI通史 | A Comprehensive AI History for Technical Professionals**

通过技术演进的历史脉络，系统构建AI知识体系。从1943年M-P神经元到2026年大模型时代，每个技术节点回答三个核心问题：**为什么出现 → 怎么工作 → 带来了什么/又卡在哪**。

*Build a systematic understanding of AI through the lens of technological evolution. From the 1943 M-P neuron to the 2026 era of large models, each technical node answers three questions: **Why it emerged → How it works → What it enabled / Where it got stuck**.*

---

## 这本书适合谁 | Who Is This For

**中文读者**：有技术功底但对AI领域空白的架构师/工程师。不需要AI基础，但需要编程和数学的基本功。

**English Readers**: Technical architects/engineers with solid programming skills but new to AI. No AI background required, but basic math and coding proficiency expected.

---

## 核心特色 | Key Features

- **时间线+技术双线交织**：每个时代的技术突破都放在历史背景中理解
- **前因后果完整追溯**：新技术为什么出现？解决了什么问题？又带来了什么新问题？
- **代码+数学双轨并行**：附录包含从零实现神经网络和Transformer的完整代码
- **2026年最新内容**：涵盖DeepSeek-R1、o3、GPT-5、Claude Mythos等最新进展

---

## 章节目录 | Table of Contents

### 第一部分：萌芽——符号与规则的时代（1940s–1970s）
### Part I: The Dawn — Symbols and Rules (1940s–1970s)

1. [机器能思考吗？（1940s–1950s）](chapters/ch01.md) — 图灵测试、M-P神经元、感知机、Logic Theorist
2. [第一次崩塌——感知机的局限与AI寒冬（1960s–1970s）](chapters/ch02.md) — XOR问题、符号AI、ELIZA、第一次AI寒冬
3. [暗流涌动——被低估的早期思想（1960s–1970s）](chapters/ch03.md) — 反向传播萌芽、Hopfield网络、统计模式识别

### 第二部分：数据与统计的时代（1980s–2000s）
### Part II: The Era of Data and Statistics (1980s–2000s)

4. [神经网络复兴——反向传播的时代（1980s）](chapters/ch04.md) — 反向传播完整推演、Neocognitron、梯度消失
5. [统计学习的黄金年代（1990s–2000s）](chapters/ch05.md) — SVM、集成方法、贝叶斯方法、特征工程
6. [深度学习的种子（2000s）](chapters/ch06.md) — 逐层预训练、GPU/CUDA、ImageNet、三要素就位

### 第三部分：深度学习的爆发（2012–2017）
### Part III: The Deep Learning Explosion (2012–2017)

7. [AlexNet时刻——深度学习登上舞台（2012）](chapters/ch07.md) — AlexNet、ReLU、Dropout、从特征工程到特征学习
8. [CNN的进化——视觉理解的深化（2013–2015）](chapters/ch08.md) — VGGNet、GoogLeNet、ResNet、目标检测
9. [序列的挑战——RNN、LSTM与注意力机制的萌芽（2014–2017）](chapters/ch09.md) — RNN、LSTM、Seq2Seq、Bahdanau注意力
10. [GAN——生成与对抗的思想（2014–2017）](chapters/ch10.md) — GAN原理、DCGAN/WGAN/StyleGAN、从识别到创造

### 第四部分：Transformer与大模型时代（2017–2022）
### Part IV: The Transformer and Large Model Era (2017–2022)

11. [Attention Is All You Need——Transformer的革命（2017）](chapters/ch11.md) — 自注意力、多头注意力、位置编码、编码器-解码器
12. [预训练语言模型——从BERT到GPT（2018–2019）](chapters/ch12.md) — Word2Vec→ELMo→BERT/GPT、预训练+微调、两条路线分化
13. [规模法则——大就是好吗？（2020–2021）](chapters/ch13.md) — GPT-3、涌现能力、Scaling Laws、MoE、Codex
14. [对齐——让AI听话（2020–2022）](chapters/ch14.md) — RLHF三步流程、InstructGPT、Constitutional AI、对齐的代价

### 第五部分：大模型的爆发与通用AI之路（2022–2026）
### Part V: The Explosion of LLMs and the Path to AGI (2022–2026)

15. [ChatGPT时刻——AI走向大众（2022–2023）](chapters/ch15.md) — ChatGPT、GPT-4多模态、开源模型崛起
16. [推理与思维链——让AI"思考"（2023–2024）](chapters/ch16.md) — CoT、搜索式推理、o1推理模型、test-time compute
17. [多模态与Agent——AI走出文本（2023–2025）](chapters/ch17.md) — VLM、扩散模型、视频生成、AI Agent、MCP、具身智能
18. [2025–2026——最新格局与前沿突破](chapters/ch18.md) — DeepSeek-R1、o3、GPT-5、Claude Mythos、Meta Superintelligence Labs

### 第六部分：展望——通向何方（2026+）
### Part VI: Looking Ahead (2026+)

19. [尚未解决的问题](chapters/ch19.md) — 幻觉、持续学习、可解释性、效率、对齐深层问题
20. [通向AGI的可能路径](chapters/ch20.md) — Scaling极限、世界模型、新架构、神经符号融合、具身智能
21. [AI与社会——技术之外](chapters/ch21.md) — 就业、监管、开源闭源、军事化、人机协作、回到图灵问题

### 附录 | Appendices

- [A. 数学基础速查](appendix/apx_a_math.md) — 线性代数、概率统计、优化理论、信息论
- [B. 从零实现一个神经网络](appendix/apx_b_neural_net.md) — Python/NumPy手写反向传播
- [C. 从零实现一个Transformer](appendix/apx_c_transformer.md) — PyTorch逐行代码解析
- [D. 关键论文索引与推荐阅读](appendix/apx_d_papers.md) — 40+篇核心论文
- [E. AI发展大事记年表](appendix/apx_e_timeline.md) — 1943-2026年大事记
- [F. 术语表](appendix/apx_f_glossary.md) — 30+核心术语

### 配图 | Diagrams

- [AI技术演进时间线](assets/diagrams/timeline.md)
- [神经网络架构演进图](assets/diagrams/architecture_evolution.md)
- [AI的三次浪潮](assets/diagrams/three_waves.md)
- [大语言模型训练流水线](assets/diagrams/training_pipeline.md)
- [BERT路线 vs GPT路线](assets/diagrams/two_routes.md)

---

## 快速开始 | Quick Start

`ash
# Clone the repository
git clone https://github.com/matehubnet/AiHistory.git

# Start reading
cd AiHistory
# Begin with chapters/ch01.md
`

---

## 贡献指南 | Contributing

欢迎提交Issue和Pull Request！详见 [CONTRIBUTING.md](CONTRIBUTING.md)。

Issues and Pull Requests are welcome! See [CONTRIBUTING.md](CONTRIBUTING.md).

---

## 许可证 | License

本作品采用 [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) 许可证。自由阅读、分享、改编，只需署名。

This work is licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) — free to read, share, and adapt with attribution.

---

## 推广与分享 | Share & Spread

如果这本书对你有帮助，欢迎：

- Star ⭐ 这个仓库
- 分享给你的技术圈子
- 在掘金、知乎、V2EX等社区推荐
- 提交到相关的 Awesome 列表

If this book helped you, please:

- Star ⭐ this repository
- Share with your tech community
- Recommend on Hacker News, Reddit, LinkedIn
- Submit to relevant Awesome lists
