# International Community Promotion Materials

## Hacker News - Show HN Post

Title: Show HN: AI History - A free open-source book covering 80 years of AI from Perceptron to GPT-5 (1943-2026)

Text: I wrote a comprehensive technical history of AI that traces the full evolution from the 1943 McCulloch-Pitts neuron to 2026's large model era. Each technical node follows a consistent structure: Why it emerged → How it works → What it enabled / Where it got stuck.

21 chapters covering: perceptrons, XOR and the first AI winter, backpropagation revival, SVM era, AlexNet and deep learning explosion, CNN evolution, RNN/LSTM/attention, GANs, Transformer, BERT vs GPT, scaling laws, RLHF and alignment, ChatGPT moment, reasoning models (o1/o3/DeepSeek-R1), GPT-5, multimodal/agents, and unsolved problems + AGI paths.

Includes appendices with from-scratch implementations of a neural network (NumPy) and Transformer (PyTorch), plus a timeline of 70+ milestones and a paper index of 40+ key papers.

Free and open source under CC BY 4.0.

https://github.com/matehubnet/AiHistory

---

## Reddit Posts

### r/MachineLearning

Title: [P] AI History: From Perceptron to LLMs - A free CC BY 4.0 book covering 80+ years of AI technical evolution

Text: I've written a comprehensive technical history of AI covering the full evolution from 1943 to 2026. The book is structured around a consistent framework for each technology: Why it emerged → How it works → What it enabled / Where it got stuck.

This means you don't just learn what a Transformer is - you learn why RNNs needed to be replaced, how self-attention solves the parallelization problem, and what new limitations Transformers introduce (O(n²) complexity, positional encoding as a patch).

Key features:
- 21 chapters from M-P neuron to GPT-5 and world models
- Code appendices: from-scratch neural network (NumPy) and Transformer (PyTorch)
- Covers 2025-2026 developments: DeepSeek-R1, o3, GPT-5, Claude Mythos, Cosmos 3
- 40+ key papers indexed with context
- CC BY 4.0 - free to read, share, and adapt

https://github.com/matehubnet/AiHistory

---

### r/learnmachinelearning

Title: I wrote a free book to help engineers systematically learn AI through its history - from perceptrons to GPT-5

Text: If you're an engineer/programmer who wants to understand AI but finds the landscape overwhelming, I wrote something that might help.

"AI History" traces the complete technical evolution from 1943 to 2026. Instead of just explaining each technology in isolation, it follows a "why → how → consequences" structure. You learn:
- Why backpropagation was needed (single-layer perceptrons couldn't solve XOR)
- How it works (chain rule on computation graphs)
- What it enabled (multi-layer networks) and where it got stuck (gradient vanishing)

This approach gives you a mental map of AI - you understand not just what each thing is, but how it connects to everything else.

Free and open source: https://github.com/matehubnet/AiHistory

---

### r/LocalLLaMA

Title: Open-source AI history book covering DeepSeek-R1, GPT-5, and the full technical evolution (1943-2026)

Text: A free CC BY 4.0 book that covers the complete AI technical timeline, with special focus on the 2025-2026 developments relevant to this community:

- DeepSeek-R1: pure RL training of reasoning, MoE architecture, $6M training cost
- Open-source vs closed-source dynamics (GPT-OSS, DeepSeek MIT license)
- World models (Genie 3, Cosmos 3, JEPA)
- New architectures beyond Transformer (Mamba/SSM, MoT)

Each chapter follows: why it emerged → how it works → what it enabled / where it got stuck.

https://github.com/matehubnet/AiHistory

---

## Twitter/X Thread Templates

### Thread 1: AI in 20 tweets (1/20)

🧵 AI History in 20 tweets: from 1943 to 2026.

1/ 1943: McCulloch-Pitts neuron - first mathematical model of neural computation. Binary logic gates made of neurons. No learning yet.

2/ 1958: Perceptron - Rosenblatt's self-learning classifier. First proof that machines can learn from data. Hype explosion.

3/ 1969: XOR problem proves single-layer perceptrons can't solve nonlinear problems. Minsky & Papert's book triggers the first AI winter. (Rosenblatt dies in 1971, never sees the revival.)

4/ 1974: Werbos invents backpropagation in his PhD thesis. Almost no one notices.

5/ 1986: Rumelhart, Hinton & Williams popularize backpropagation. Multi-layer networks become trainable. Neural networks revive.

6/ 1995: SVM dominates. Theory guarantees + kernel trick. Neural networks considered outdated.

7/ 2006: Hinton's deep belief networks - layer-by-layer pretraining proves "deep" is feasible. "Deep Learning" starts trending.

8/ 2012: AlexNet wins ImageNet. Error rate drops from 26% to 16%. Computer vision switches to deep learning overnight.

9/ 2014: GAN (Goodfellow) - generator vs discriminator. AI can create realistic images for the first time.

10/ 2014: Bahdanau attention - decoder dynamically focuses on different source positions. The prelude to Transformer.

11/ 2017: "Attention Is All You Need" - Transformer replaces RNN. Self-attention: every position directly connects to every other. Full parallelization on GPU.

12/ 2018: BERT (bidirectional) vs GPT-1 (autoregressive). Two routes diverge. BERT sweeps 11 benchmarks. Everyone bets on BERT.

13/ 2020: GPT-3 (175B params). In-context learning emerges. Scaling Laws published. Arms race begins.

14/ 2022: ChatGPT. 5 days: 1M users. 2 months: 100M users. GPT-3.5 + RLHF. The product was right, not just the tech.

15/ 2022: RLHF - reward model learns human preferences, PPO fine-tunes LLM. Alignment makes models useful and safe. But alignment tax exists.

16/ 2024: o1 - first "thinking" model. Generates chain of thought before answering. AIME 83% (GPT-4o: 13%). Test-time compute becomes new paradigm.

17/ 2025 Jan: DeepSeek-R1. Pure RL training. MoE architecture. $6M cost. MIT license. Nvidia loses $600B market cap in one day. "Sputnik moment."

18/ 2025 Aug: GPT-5. Not one model, but a system. Fast model + reasoning model + router + agent. Users don't choose models anymore.

19/ 2026: World models everywhere. Genie 3, Cosmos 3, JEPA/AMI Labs ($1.03B funding). AI tries to understand physics, not just text.

20/ The pattern repeats: breakthrough → hype → limitation → winter → next breakthrough. Each winter births the next revolution.

📖 Full book (21 chapters, CC BY 4.0): https://github.com/matehubnet/AiHistory

---

### Thread 2: Why GPT beat BERT (shorter)

🧵 Why the GPT (generative) route beat the BERT (understanding) route - despite BERT being stronger in 2018:

1/ BERT uses masked language model: hide words, predict them from context. Bidirectional. Great for "understanding" tasks.

2/ GPT uses autoregressive model: predict next word from left context only. Unidirectional. Seems weaker.

3/ But generating text is HARDER than filling blanks. It forces deeper representations. You must plan ahead to write coherent text.

4/ BERT's MLM objective has an upper bound - there's a limit to how hard "fill in the blank" can get. Scaling hits diminishing returns early.

5/ GPT's autoregressive objective has no such bound - better language models always predict next tokens more accurately. Scaling Laws confirm.

6/ Zero-shot/few-shot comes naturally to generators. Describe the task in natural language → model does it. BERT needs fine-tuning for every task.

7/ RLHF works on generators. You can reinforce good generation behavior. You can't RLHF "fill in the blank."

8/ Lesson: harder tasks force deeper understanding. In AI, stronger constraints often produce stronger capabilities.

📖 Full analysis: https://github.com/matehubnet/AiHistory

---

## LinkedIn Post

Title: The AI knowledge gap for engineers - and a free resource that bridges it

I've been watching a pattern: experienced engineers who want to understand AI but find the landscape overwhelming. There's too much to learn, too many disconnected tutorials, too little context.

I wrote a free open-source book to address this: "AI History: From Perceptron to Large Language Models."

The approach is different from most AI resources. Instead of teaching each technology in isolation, it follows a consistent structure for every innovation:

Why it emerged → How it works → What it enabled / Where it got stuck

This gives you a mental map. You don't just learn what a Transformer is - you understand why RNNs needed replacement, how self-attention solves the parallelization bottleneck, and what new problems Transformers create.

21 chapters from 1943 to 2026. Code appendices. CC BY 4.0.

https://github.com/matehubnet/AiHistory

If you're a technical professional looking to systematically build your AI knowledge, I'd love your feedback.
