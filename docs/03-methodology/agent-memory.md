# Agent Memory: Workflow, Not Infrastructure

Most multi-agent fiction tools treat memory as a database problem. This methodology treats it as a workflow problem. Here's the design.

---

## The four layers of memory

| Layer | What it holds | Where it lives | Lifetime |
|------|---------------|----------------|---------|
| **L1. Persona** | Who the agent IS (job, boundaries, output format) | `SOUL.md` per agent workspace | Project-long, rarely edited |
| **L2. Project dossier** | Locked facts (world rules, character profiles, antagonist network) | `briefing_dossier.md`, auto-loaded into input packages | Project-long, updated by author |
| **L3. Session input** | THIS session's brief + locked facts + previous-chapter context | `00_输入包.md` per session | Session-only |
| **L4. Cross-agent output** | What other agents in the same session said | Captain reads R1 + R2 outputs before ruling | Session-only |

No vector DB. No RAG. **The author curates the slices.**

## Why curation beats retrieval

A vector DB retrieving "the most similar context" to the current chapter will give you the wrong slice ~30% of the time when the novel is doing something **structurally new** — a turn, a reveal, a pivot. Long-form fiction breaks vector retrieval assumptions exactly when it matters most.

Curation — the author choosing what facts to inject — is **slow but correct**. The cost is minutes per session. The benefit is that the agents don't hallucinate a different version of the novel.

Counter-argument: "but curation doesn't scale." Correct. It doesn't need to. **Long-form fiction is the wrong domain to scale memory acquisition over.** The author already knows what matters. The cost of writing 100k words dwarfs the cost of writing input packages.

## Model selection as memory: the cognitive-flavor argument

Memory isn't only what an agent **has access to**. It's also what an agent **naturally pays attention to**. Model choice shapes effective memory.

Empirical heuristics (developed over ~80 sessions, single author, mixed genres):

| Pattern | Pick this model | Don't pick |
|---------|-----------------|-----------|
| Need broad surface of options early | qwen3-max | claude-sonnet (commits early) |
| Need sharp tear-down of weak structure | glm-4.7 | gpt-4o (too polite) |
| Need taste judgment, not structure logic | kimi-k2.5 | qwen3 (too symmetric, gives N options not a verdict) |
| Need fast pattern matching on prose tics | gemini-2.5-flash | larger models (overkill, slow, no real gain) |
| Need synthesis without flattening | claude-sonnet-4-6 | majority-vote logic / GPT-style averaging |

These are **judgment heuristics, not benchmark claims**. The reader can test against their own data and disagree — the point is that model-task matching is itself craft, not config.

A working principle: **never pick a model on benchmark, always pick on observed cognitive flavor**. Benchmarks tell you ceiling; the role asks about distribution. Different problems.

## The shared input package trick

For 4-agent outline discussions, all agents read **the same** input package in Round 1. This sounds redundant. It's not.

The shared substrate means:

- Disagreement comes from interpretation, not from missing data
- Round 2 cross-challenges become substantive (agents can't dodge by claiming "but I didn't see X")
- Captain's consolidation is doable — the disagreement surface is bounded

If agents had different inputs, the captain would be solving "which agent saw what" before "which is right". You'd lose half the round to bookkeeping.

## The "do not debate" list

Some facts in the dossier are marked **不可改动** (cannot be changed). The agents are not allowed to propose alternatives.

This sounds restrictive. It is. It's also the entire reason the system works.

Without explicit forbidden lists, a diverger will eventually propose burning down a character the author has already committed to. Then the critic has to re-argue first principles every session. Locking facts in the input package eliminates this entire failure mode.

**Memory isn't just what's in scope — it's also what's explicitly out of scope.**

This is the move that engineering-led memory systems miss. They optimize for "what should the agent see", not "what should the agent treat as settled". The second list is more important.

## What this is not

- Not a long-context LLM trick (8k contexts work fine for the per-session slice)
- Not a RAG implementation (curation, not retrieval)
- Not auto-summarization (the dossier is hand-curated, edited as the project evolves)

It's **a workflow where the author maintains the memory shape**, and the agents work within that shape.

The cost is author time. The return is agents that don't drift.

---

→ [Back to architecture](../02-architecture.md)
→ Next: `agent-consistency.md` (v0.2)
