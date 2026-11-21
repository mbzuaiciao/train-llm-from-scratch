
---
https://chatgpt.com/c/6a276dc6-8410-83e8-9e9b-02d78b93913c

Start with these three:

### 1. Neural Networks: Zero to Hero (Foundation)

[nn-zero-to-hero GitHub](https://github.com/karpathy/nn-zero-to-hero?utm_source=chatgpt.com)

This covers:

```text
micrograd
↓
backpropagation
↓
MLPs
↓
BatchNorm
↓
WaveNet
↓
tokenization
↓
language models
```

This is where you build the intuition. ([GitHub](https://github.com/karpathy/nn-zero-to-hero?utm_source=chatgpt.com "karpathy/nn-zero-to-hero: Neural Networks"))

---

### 2. Let's Build GPT (The Video)

[Let's Build GPT YouTube](https://www.youtube.com/watch?v=kCc8FmEb1nY&utm_source=chatgpt.com)

This is the famous ~4-hour transformer walkthrough.

He implements:

```text
embeddings
↓
attention
↓
multi-head attention
↓
transformer blocks
↓
GPT
↓
training
↓
generation
```

from scratch in PyTorch. ([YouTube](https://www.youtube.com/watch?v=kCc8FmEb1nY&utm_source=chatgpt.com "Let's build GPT: from scratch, in code, spelled out."))

---

### 3. build-nanogpt (Companion Repo)

[build-nanogpt GitHub](https://github.com/karpathy/build-nanogpt?utm_source=chatgpt.com)

This is the repo that accompanies the newer GPT-building video. The commits are intentionally incremental so you can step through the evolution of the model. ([GitHub](https://github.com/karpathy/build-nanogpt?utm_source=chatgpt.com "Video+code lecture on building nanoGPT from scratch"))

---

### Later (after you've finished the above)

#### nanoGPT

[nanoGPT GitHub](https://github.com/karpathy/nanoGPT?utm_source=chatgpt.com)

This is closer to a real training framework and is less educational than `build-nanogpt`. Karpathy himself describes it as prioritizing practical training and finetuning over teaching. ([GitHub](https://github.com/karpathy/nanogpt?utm_source=chatgpt.com "karpathy/nanoGPT: The simplest, fastest repository ..."))

---

If I were designing a study plan for you:

```text
Week 1
├── Zero to Hero lectures 1-4
├── Take Obsidian notes
└── Reimplement key code

Week 2
├── Let's Build GPT
├── Follow build-nanogpt
└── Draw tensor shapes by hand

Week 3
├── Fareed's transformer code
├── Compare against Karpathy
└── Identify architectural differences

Week 4
├── POST_TRAINING.md
├── SFT
├── DPO
└── GRPO
```

That sequence will give you a much stronger foundation than starting directly with Fareed's repo.

---
https://gemini.google.com/app/71669cf9e3c7105c

Yes, Andrej Karpathy's educational resources are widely considered the gold standard for understanding Large Language Models from the ground up. He has released a few distinct tutorials depending on how deep you want to go into the code versus the high-level architecture.

Here is a breakdown of his primary LLM tutorials and their key insights:

### 1. "Intro to Large Language Models" (The High-Level Overview)

A non-technical, high-level introductory talk (about 1 hour) that explains what an LLM actually is.

- **The Two-File Analogy:** He explains that an LLM fundamentally consists of just two files: a **parameters file** (the weights containing the network's data) and a **run file** (typically written in C or Python to execute the neural network forward pass).
    
- **The Two Stages of Training:**
    
    1. **Pre-training:** Consumes massive computational resources (millions of dollars) to scan internet text and build a powerful "next-token predictor" or autocomplete engine.
        
    2. **Post-training (Fine-tuning & RLHF):** Uses structured human-assistant conversations to transform that raw document generator into a helpful, conversational assistant (like ChatGPT or Claude).
        
- **System 1 vs. System 2 Thinking:** Karpathy notes that current LLMs operate entirely via "System 1" thinking—instantly calculating the next word using fixed computation per token. The frontier of AI focuses on "System 2" thinking, allowing models time to deliberate, use a "tree of thoughts," and self-correct before responding.
    

### 2. "Deep Dive into LLMs like ChatGPT" (The Architectural Breakdown)

A comprehensive, ~3.5-hour deep dive exploring the actual mechanics behind modern transformer pipelines.

- **Tokenization:** Explains how raw text is converted into integers using Byte Pair Encoding (BPE), highlighting why models struggle with simple arithmetic or counting characters (because the model only sees integer tokens, not raw characters).
    
- **Working Memory vs. Parametric Memory:** Knowledge stored in the weights is abstract and prone to vague recollections (hallucinations), whereas information provided directly inside the context window serves as active, high-fidelity working memory.
    
- **Why Models Need "Time to Think":** When a model is forced to answer a complex problem instantly, it often fails. Allowing it to generate intermediate reasoning tokens (e.g., "thinking blocks" or chain-of-thought steps) distributes the necessary computation across multiple tokens, vastly improving accuracy.
    

### 3. Practical Coding Implementations: `nanoGPT` and `llm.c`

For developers wanting to build and train models locally:

- **Let's build GPT: from scratch, in code, spelled out:** A legendary 2-hour video tutorial where he builds a clean, readable, character-level GPT transformer based on the _Attention Is All You Need_ paper using PyTorch.
    
- **`llm.c` GitHub Repository:** A project where he implements full GPT-2 training completely from scratch in raw C/CUDA without heavy frameworks like PyTorch, optimizing for performance and absolute transparency of the underlying math.
    

### 4. The "LLM Wiki" Workflow

Karpathy popularized a highly practical workflow for an AI-maintained personal knowledge base. Instead of relying on a standard vector database (RAG) that searches from scratch on every query, he utilizes an AI coding agent to actively build, cross-link, and lint a folder of structured Markdown files (`.md`) inside a vault like Obsidian. This allows the local text knowledge to compound into a mini-encyclopedia over time.

[Andrej Karpathy's Intro to Large Language Models](https://www.youtube.com/watch?v=zjkBMFhNj_g) provides an incredible foundational overview of how models are trained and why they behave the way they do.