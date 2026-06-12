# Genre Adaptation

> Status: **v0.1 skeleton** · fully expanded in v0.4 when the second genre bucket (mystery) goes live with cases.
> Maintained by 翎 · syncs with [`DECISIONS.md`](../DECISIONS.md) D10 (genre buckets max 3).

This document is the design-principles view of how the lab's methodology adapts across genres. **For v0.1 it is a skeleton** — the full adaptation guide requires multiple genres in production to write honestly. The skeleton below states the principles and flags what gets expanded when v0.4 lands the second case.

---

## What stays constant across genres

These are **universal** to the lab's methodology and never change:

| Layer | Why it's invariant |
|-------|---------------------|
| Two cooperating agent teams (outline + prose review) | The split itself is the core design — separating structural debate from prose audit. See [`02-architecture.md`](./02-architecture.md). |
| Persistent SOULs as identity-not-task | Identity-driven personas resist drift across genres. See [`agent-consistency.md`](./03-methodology/agent-consistency.md). |
| Memory-as-workflow (curated input package, no vector retrieval) | Long-form fiction breaks vector retrieval. See [`agent-memory.md`](./03-methodology/agent-memory.md). |
| The "do not debate" list pattern | Each genre has its own list, but every genre needs one. |
| Refusal rate as a health metric | Paired-agent tension needs refusals to stay productive. See [`agent-character-tension.md`](./03-methodology/agent-character-tension.md). |

## What changes per genre

Three concrete adaptation surfaces:

### 1. SOUL persona tuning

Each agent's SOUL retains its **structural shape** (single-sentence job, hard boundaries, bounded output) but its **dimensional focus** shifts by genre:

| Agent role | folklore-mystery focus | mystery focus (v0.4) | psychological-character-study focus (v0.4) |
|-----------|------------------------|---------------------|--------------------------------------------|
| diverger | Atmosphere + symbolic-chain divergence | Clue-state + suspect-graph divergence | Internal-state + revelation-pacing divergence |
| critic | Logic of myth-causality | Logic of fair-play deduction | Logic of psychological causation |
| aesthete | Numinous restraint, weight of objects | Mystery-grammar tension, fair-play satisfaction | Interiority compression, withheld disclosure |
| voice-check | Period register, voice as character | Detective + suspect voice distinctiveness | Internal-monologue vs external-speech contrast |
| forbidden-check | "Explain the supernatural" forbidden | "Withhold clue from reader" forbidden (本格) | "Diagnose the character" forbidden |

These are first-pass projections. They will be revised when v0.4 lands the second genre case.

### 2. The "do not debate" list

Each genre has its own non-fungible commitments that get locked into the input package:

- **folklore-mystery (旁证体 baseline)** — see [`case-旁证体.md`](../examples/case-studies/01-folklore-mystery/case-旁证体.md) "Craft methodology": seven hooks including 物件叙事链, 双对照, 工艺红线
- **mystery (本格 / 社会派, planned v0.4)** — fair-play vs social-critique foundational tension; specific list TBD
- **psychological-character-study (proposed v0.4)** — TBD

The act of writing this list per genre **is itself the adaptation work** — most of the time spent adapting to a new genre is spent surfacing what the author refuses to compromise on, not redesigning the agents.

### 3. Evaluation rubric

The 7 metrics defined in [`agent-consistency.md`](./03-methodology/agent-consistency.md) (4 content-level) and [`DECISIONS.md`](../DECISIONS.md) D12 (3 system-level) remain the same, but their **operationalization** shifts:

- "Did character voice hold?" — Same metric. The voice baseline is genre-specific.
- "Did plot causality hold?" — Same metric. The causality grammar is genre-specific (myth-logic vs deductive-logic vs psychological-logic).
- "Did the do-not-debate list hold?" — Same metric. The list is genre-specific (by definition).

The system-level metrics (actionability rate / inter-agent agreement / coherence over sessions) are **genre-invariant** — they measure the workflow itself, not the work product.

## What this means in practice

To adapt the workflow to a new genre, the author does **not** redesign the agents. They:

1. Identify the genre's foundational tension (what is the work refusing to flatten?)
2. Write the new "do not debate" list
3. Tune each SOUL's dimensional focus (the table above)
4. Surface 2-3 genre-specific forbidden patterns for forbidden-check
5. Run a single chapter and check refusal rates — if any agent's refusal rate is 0, the adaptation is incomplete

This is typically **1–2 weeks of work**, not a months-long redesign — because the structural pattern is reused.

## What this v0.1 skeleton does NOT include

- A second worked example. The second case (mystery) lands in v0.4.
- Empirically validated adaptation costs. We claim "1–2 weeks" but have only one genre in production.
- A failure-mode catalog per genre. Will land when the 03-TBD bucket runs its first session.

## Read this in order

If you arrived here trying to understand genre handling for a specific genre:

1. Start with [`case-旁证体.md`](../examples/case-studies/01-folklore-mystery/case-旁证体.md) for the craft baseline of the live genre
2. Then read [`agent-character-tension.md`](./03-methodology/agent-character-tension.md) for the design pattern that handles genre-specific tension
3. This document gives you the rest of the adaptation logic — but the live examples are where you check whether the logic actually works

---

→ Back to [`02-architecture.md`](./02-architecture.md)
→ Related: [`agent-character-tension.md`](./03-methodology/agent-character-tension.md), [`DECISIONS.md` D10](../DECISIONS.md)
