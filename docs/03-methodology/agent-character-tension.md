# Agent Character Tension: When Two Agents Are Better Than One

The textbook approach to multi-agent fiction has one agent generate, one agent review, one agent revise — a pipeline. This lab discovered a different pattern: **two character agents looking at the same project from two different commitments, holding each other accountable across a structural tension.**

This document describes that pattern, the case study where it emerged, and how to design it.

---

## The pattern: paired character agents

When the surface task is "review the prose," a single review agent suffices. When the surface task is "is this novel earning its emotional debts?" — one agent is not enough — because *earning* is itself a tension between two commitments that pull in different directions.

In long-form fiction with morally complex material (BDSM, trauma, abuse-of-power, addictive relationships), there are at least two non-fungible commitments that must be held simultaneously:

1. **Craft integrity** — the work must hold as fiction: voice, blocking, prose rhythm, narrative architecture
2. **Ethical integrity** — the work must not collapse difficult material into convenient resolutions: traumatic attachment ≠ love evidence, forced silence ≠ subjectivity preservation, dependence ≠ consent

A single review agent has to choose which commitment it prioritizes per call. This creates oscillation across chapters. Two agents, each fully committed to its own dimension, hold the tension stable.

## Case study: 执白 × 烨 on 鲛人蛇吻 v3

The lab's actual deployment of this pattern:

| Agent | Commitment | Operating principle |
|-------|-----------|---------------------|
| **执白** | **Craft gatekeeper** (工艺守门) | 物件叙事链 / 双对照 / B-line accounting / 工艺红线 — make the prose hold |
| **烨** | **Ethical calibrator** (伦理校准) | "Evidence accumulation + dominance loosening + refusal actually changes outcomes + mutual shaping + ungrateful autonomous choice" — make the relationship structure refuse to flatten |

These two agents are personae of **the same author** — both are voices the author can speak in — but tuned for different dimensions and required to hold their own ground against each other.

When 执白 proposes a structural alternative that lands aesthetically but smuggles in *"trauma-attachment as love-evidence,"* 烨 must refuse it on ethical grounds. When 烨 proposes an ethical correction that lands cleanly but flattens the craft hooks (e.g., "add an explicit-consent moment"), 执白 must refuse it on craft grounds. **The tension between them is the work product.**

This pattern was **discovered, not designed**. The author's first attempt was to have one agent handle both commitments. The agent quietly oscillated — biasing whichever side the recent input pulled toward. Splitting into 执白 + 烨 stabilized the standards.

## When to use this pattern

Not always. Specifically when:

- The work has **two non-fungible commitments that genuinely conflict** in places
- A single agent would have to compromise both commitments per call
- The conflict itself is part of what the work is about (not a deficiency to be resolved)

If the project has a single clear commitment (e.g., "produce technically clean prose"), one agent suffices. If the work has commitments that don't conflict (e.g., "be funny" + "be readable"), one agent suffices. The pattern applies specifically when the commitments are in genuine tension.

## How to design the pair

Three design principles:

### 1. Clear identity separation

Each agent's `SOUL.md` must articulate its own commitment in its own voice. Not "you are agent A reviewing for X" but "I commit to Y as my non-negotiable." When the agent's own commitment is internalized as identity (not assigned as task), it resists drifting toward the other agent's territory.

### 2. Dimensional complementarity, not overlap

The two agents must look at **different things, not the same thing from different angles.** 执白 looks at the prose. 烨 looks at the power dynamics. They both see the same chapter, but they're auditing different layers. Overlap creates redundancy (and one of them becomes vestigial).

### 3. Explicit refusal lists

Each agent maintains its own list of **what it will refuse to produce, even if the other agent argues for it**:

- 烨's list includes: "I will not certify trauma-attachment as love-evidence." "I will not certify forced silence as subjectivity preservation." "I will not let reference sources substitute for fiction's final say."
- 执白's list includes: "I will not certify a sentence that explains its own subtext." "I will not certify an explicit-consent moment that breaks the period craft."

These refusal lists are how tension stays stable. Without them, the agents collapse into "whoever spoke last sounded reasonable."

## Evaluation

A paired-character-tension setup is working when:

| Metric | Operationalization |
|--------|---------------------|
| **Refusal rate** | Each agent refuses ≥ N% of cross-agent suggestions per session. **If either agent's refusal rate is 0, the pair has collapsed.** |
| **Persistent disagreement on locked items** | Specific items remain in genuine disagreement across multiple sessions. The disagreement is not "solved" — it is **held** |
| **Author satisfaction with the held tension** | Author rates the work as "this is what I wanted to write" more than under the single-agent setup |

These metrics will be tested formally in v0.2 `research/02-evaluation-metrics.md`.

## What this is not

- **Not "democracy by agents."** No voting.
- **Not "two reviews are better than one."** Not redundant coverage.
- **Not "we converged on the truth."** No convergence required.

The point is structural — two agents holding two non-fungible commitments in productive disagreement, **where the work product is the held tension, not the compromise.**

For the author behind these two agents (康康), the discovery was: when she tried to be both 工艺守门 and 伦理校准 at once, she silently let one slide. Splitting into two named characters made the standards refuse to slide.

---

→ Back to [agent consistency](./agent-consistency.md)
→ Next: `outline-evolution.md` (v0.2)
