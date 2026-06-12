# Agent Handoff: How State Crosses Session Boundaries

> Status: **v0.1 skeleton** · expanded in v0.2 with a chapter-level walkthrough.

Sessions end. Tokens run out. Models update. The author goes to sleep. The work continues. **The handoff is what makes that continuation possible without losing the work's accumulated judgment.**

This document describes the lab's three layers of handoff and why they're designed the way they are.

---

## The three layers

| Layer | Who hands off to whom | How |
|-------|----------------------|-----|
| **Intra-session** | Sub-agents → Captain | Captain reads all sub-agent outputs as input |
| **Inter-session (same agent)** | Session N → Session N+1 | Via persistent SOUL (identity) + per-session input package (curated state) |
| **Author ↔ Agent** | Human → Agent (and reverse) | The human is the messenger; markdown files are the medium |

The third layer is the most contested design choice and the one the lab argues hardest for.

## Layer 1: Intra-session (sub-agents → captain)

When the 4-agent outline team runs R1 + R2 + arbitration, all five outputs (diverger R1, critic R1, critic R2, aesthete R1, aesthete R2) flow into the captain's input. The captain doesn't re-invoke the sub-agents; she reads what they already wrote.

This pattern matters because:

- The captain is **consolidating findings**, not re-discovering them — different cognitive task
- The trail (R1 + R2) becomes part of the captain's reasoning surface — she can cite specific disagreements as part of her ruling
- The handoff is **file-based, not function-call-based** — meaning the trail is preserved as an artifact for the author to audit

See [`../../examples/workflow-template/4-agent-outline/orchestration.md`](../../examples/workflow-template/4-agent-outline/orchestration.md) for the implementation skeleton.

## Layer 2: Inter-session (same agent, next time)

A diverger agent in session 12 needs to know what was decided in session 11 — but **not by re-reading session 11's transcript**. That would be too much context, and most of it would be irrelevant.

Instead, the diverger reads:

1. Their persistent `SOUL.md` (who they are — doesn't change)
2. The current session's input package, which includes:
   - Locked facts (per the do-not-debate list, see [`agent-consistency.md`](./agent-consistency.md))
   - The previous session's ruling (`07_decision.md` from the previous cycle) — **distilled, not raw**
   - The current author brief

This is **memory as workflow, not infrastructure** (see [`agent-memory.md`](./agent-memory.md)). The author curates what carries forward; the agent doesn't auto-load history.

Why this matters: long-form fiction makes *"structurally new"* moves — a reveal, a turn, a betrayal. At those moments, what carried the agent successfully through the last 30 sessions becomes **actively misleading**. Auto-loaded history would reinforce the wrong patterns. Curated handoff forces the author to re-state what's still true and what's now different.

## Layer 3: Author ↔ Agent (human-as-messenger)

This is the lab's most controversial design choice. The industry wants autonomous agents talking directly to each other. The lab insists on routing through the author.

Mechanically: **agents in different sessions never directly read each other's outputs.** The author reads them, decides what to carry forward, and writes the input package for the next session.

Why this matters:

1. **The author is the source of judgment about when a "structurally new move" is happening** — see Layer 2. An autonomous orchestrator can't tell when to break with precedent; the author can.
2. **The audit trail is comprehensive** — every cross-session handoff goes through a human checkpoint. There's no "the agent just decided" black box.
3. **The author stays in the loop by design**, not as an afterthought — see the lab's broader argument in [`../01-why.md`](../01-why.md).

The cost: it's slow. The author spends 30–60 minutes per session writing the input package. For a 200-session novel, that's 100–200 hours of "messenger" work.

The return: **the author's judgment is on every page. The novel is hers, not the agents'.**

## The input package as canonical handoff format

Both Layer 2 (inter-session) and Layer 3 (author-mediated) use the same physical format: `00_输入包.md`. This is **deliberate**. One format for handoff means one place to look when something goes wrong.

The package's structure:

```
1. 固定事实源 (locked facts — explicit do-not-debate)
2. 角色 / 情感锚点 (character / CP design — locked)
3. 项目速查手册 (auto-loaded briefing dossier — ~3000 words)
4. 外部主笔输入 (the brief for THIS session only)
5. 禁止改动 (explicit out-of-scope for this session)
6. 期望输出 (output format spec)
```

The author writes (4) and (5) each session. The other four are stable across sessions but **re-included so the agent doesn't have to "remember" anything**.

## What goes wrong when handoff is sloppy

- **Stale locked facts** — character behavior the author has since changed, but the package still locks the old version. Agent dutifully writes against the old rules.
- **Missing do-not-debate items** — agent re-proposes structural changes the author has already committed against. Author wastes a session re-arguing first principles.
- **Auto-loaded history without curation** — agent treats episodes from session 5 as still-active context in session 50, where the project has moved past them.
- **No briefing dossier** — agent makes up plausible-sounding details that contradict the locked world.

Most "AI agent loses the plot" complaints reduce to one of these. **The handoff layer is what prevents them.**

## Why this differs from autonomous-orchestrator patterns

LangGraph's persistent-state graphs, AutoGen's conversation history, CrewAI's task delegation — they all assume the orchestrator can manage handoff. The lab's position is that **for long-form creative work specifically**, the orchestrator can't:

- The orchestrator doesn't know which old facts are now stale (the author does)
- The orchestrator can't tell when "this time it's structurally different" (the author can)
- The orchestrator has no way to audit its own handoff decisions in the way an author can audit a curated input package

This is **not** a claim that human-mediated handoff is better in general. It is a claim that for the specific demands of long-form fiction — where the work product is the held tension between many specific judgments — human-mediated handoff is the only one that doesn't silently drift.

For shorter-horizon or less judgment-dense work, autonomous handoff probably is better. The lab's argument is domain-specific.

## What this v0.1 skeleton does NOT include

- A worked walkthrough of an actual handoff cycle. Lands in v0.2.
- Tooling for *partial* automation of input-package generation from prior state — the lab argues against *full* automation here (Layer 3 needs the author), but a "draft-then-author-edits" assist could be valuable. To be explored.
- Comparison with autonomous-orchestrator handoff patterns from real LangGraph / AutoGen / CrewAI runs. Lands in v0.3 `research/03-framework-comparison/`.

---

→ Back to [`agent-memory.md`](./agent-memory.md)
→ Related: [`agent-consistency.md`](./agent-consistency.md), [`agent-character-tension.md`](./agent-character-tension.md), [`outline-evolution.md`](./outline-evolution.md), [`prose-evolution.md`](./prose-evolution.md)
→ Implementation: [`../../examples/workflow-template/4-agent-outline/orchestration.md`](../../examples/workflow-template/4-agent-outline/orchestration.md)
