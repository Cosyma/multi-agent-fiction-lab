# Why this lab exists

**TL;DR** — AI writing tools treat the hard problems (consistency, memory, voice) as **infrastructure issues**. This lab treats them as **workflow issues**. The difference is structural, not stylistic.

---

## The market today

AI fiction tools split into two clusters:

| Cluster | Examples | What they do well | Where they fall short for long-form |
|---------|----------|-------------------|-------------------------------------|
| Writing assistants | Sudowrite, NovelAI, 彩云小梦, 妙笔 | Sentence-level fluency, brainstorm prompts, style emulation | Character drift, plot incoherence past 50k words, no review loop |
| Agent frameworks | LangGraph, AutoGen, CrewAI, OpenAI Swarm | Tool orchestration, role assignment, structured I/O | Generic agent roles, no domain-specific cognitive matching, no creative arbitration |

Neither is designed for the actual problem: **a novel that holds up across 100k+ words.**

## The gap that matters

Long-form fiction needs three things to hold:

1. **Character consistency across chapters** — voice stays voice, doesn't drift toward the author's default
2. **Plot causality across acts** — events earn each other, not just chain
3. **Aesthetic coherence across volumes** — taste stays taste, doesn't regress to the mean

Infrastructure-first approaches address these as data problems (more context, better embeddings, finer-tuned models). They don't scale, because the underlying issue is **judgment**, not retrieval.

## What this lab does instead

Treats the problem as **a small team of specialists with explicit handoffs**:

- **A divergent thinker proposes structures** — broad surface, not committed
- **A critic finds where structure breaks** — sharp adversarial pass
- **An aesthete judges what's worth saving** — taste arbitration
- **A captain rules and orders changes** — consolidation, prioritization

The same shape applies at the prose layer: **rhythm / blocking / voice / forbidden / captain**.

The "agents" are not interchangeable LLM workers. **Each is a model picked for its cognitive flavor**:

| Role | Model | Why |
|------|-------|-----|
| diverger | qwen3-max | broad surface, comfortable with multiple co-existing options |
| critic | glm-4.7 | sharp, doesn't soften, finds breaks |
| aesthete | kimi-k2.5 | taste-forward, judges quality not just structure |
| forbidden | gemini-2.5-flash | fast pattern matching for stylistic violations |
| captain | claude-sonnet-4-6 | synthesis without flattening |

This is the differentiator. Tools treat models as substitutable. **A lab treats model selection as craft.**

## Why PM, not engineer

An engineer asks "how do I make the system work". A PM asks "what is the system supposed to produce, for whom, with what trade-offs".

The choices in this lab — five agents not three, two-round debate not single-pass, captain consolidation not voting — are PM choices. They optimize for **what serves the novel**, not for what's easy to build.

This is also why the methodology is documented as a methodology, not packaged as a product. Productizing would force premature commitments. The lab stays a lab so the workflow can keep evolving.

## What this lab is not

- Not a tool to sell
- Not a generic framework to fork
- Not a research lab funded by anyone
- Not finished

It's a working methodology kept open — for the few people who'd find this exact intersection useful.

→ Read [`02-architecture.md`](./02-architecture.md) for the actual system.
