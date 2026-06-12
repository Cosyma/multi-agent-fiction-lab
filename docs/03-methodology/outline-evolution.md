# Outline Evolution: How a Volume Outline Iterates

> Status: **v0.1 skeleton** · expanded in v0.2 with a walkthrough of an actual iteration session.

A single-pass outline is the failure mode of long-form fiction. A volume that survives is one whose outline has been **iteratively challenged, defended, partially abandoned, and rebuilt** — usually multiple times. This document describes the pattern this lab uses for outline iteration.

---

## What outline iteration is not

It is **not** "the author writes a v1, then v2, then v3 of the outline." That's revision, not iteration.

Iteration here means: each version of the outline emerges from a **structured argument** with explicit roles — divergent proposals, adversarial criticism, aesthetic arbitration, and final ruling. The argument leaves a trail. The trail is what makes the outline stable, because every choice in it has a recorded counter-argument that lost.

## The four-stage pattern

The lab's outline-iteration pattern, used in production for both 鲛人蛇吻 v2 and v3:

| Stage | Who acts | Output |
|-------|----------|--------|
| **R1: Independent first-pass** | diverger + critic + aesthete each, in isolation | 3 first-pass opinions, each written without seeing the others |
| **R2: Cross-challenge** | critic challenges diverger's R1 specifically; aesthete arbitrates between diverger's R1 and critic's R1+R2 | Disagreement surface mapped and partially resolved |
| **Captain consolidation** | wuzhui (captain) reads R1 + R2 outputs and produces summary + ruling | `06_summary.md` (deliberation trail) + `07_decision.md` (binding decision) |
| **Author review** | The human author reads the captain's ruling and decides apply / defer / rewrite | Promoted decision file → main project space + state advancement |

Each cycle of this pattern takes ~30 minutes to a few hours of agent time. Author review is typically 1–2 hours per ruling.

For implementation details see [`../../examples/workflow-template/4-agent-outline/orchestration.md`](../../examples/workflow-template/4-agent-outline/orchestration.md).

## Why this pattern instead of single-pass

Single-pass outline (one agent generates a full outline) fails in three ways:

1. **No counter-argument trail** — when the author later disagrees with a choice, there's nothing to push against
2. **Groupthink-by-default** — the single agent commits to its first plausible structure and elaborates from there
3. **No arbitration layer** — taste judgments get tangled with logic judgments, neither resolved clearly

The four-stage pattern addresses each:

1. The R1 + R2 trail **is** the counter-argument record — every losing proposal is documented with why it lost
2. Independent R1 forces three distinct first-pass surfaces; R2 turns them into adversarial dialectic
3. Aesthete arbitrates **taste**; captain rules on **structure** — keeping the two kinds of judgment separate prevents one from contaminating the other

## What "iteration" produces (across multiple cycles)

A volume outline typically goes through **3–8 iteration cycles** before reaching a stable form. Each cycle:

- Locks in some decisions → these become "do not debate" in subsequent cycles (see [`agent-consistency.md`](./agent-consistency.md))
- Opens new questions → these become the input to the next cycle's R1
- Surfaces tensions the author must resolve directly → these get promoted to the author's `{stage}_decision.md`

By cycle 3–5, most of the *structural* questions are settled. By cycle 5–8, *emotional logic* and *causality chain* are settled. The outline is then ready for prose drafting (see [`prose-evolution.md`](./prose-evolution.md), v0.2).

## What kept this from being mechanical

The pattern looks like a process diagram, but in practice each iteration's "winning" choice depends on judgment that varies by chapter:

- Sometimes the diverger's most-divergent proposal wins because the critic's objection turns out to be cosmetic
- Sometimes the critic's surface-level break is the warning sign of a deeper architectural mistake
- Sometimes the aesthete protects a proposal everyone else thought too risky

The pattern provides the **structure for judgment, not a substitute for it.** This is why model selection matters — the diverger needs surface breadth, the critic needs sharpness, the aesthete needs taste, the captain needs synthesis. See `DECISIONS.md` D07 (model selection as criteria, not conclusion).

## What this v0.1 skeleton does NOT include

- A worked walkthrough of an actual outline-iteration session. **Lands in v0.2** alongside the `case-鲛人蛇吻.md` excerpt — the workflow showed itself producing the Ch37 sequence, and the iteration trail will be excerpted there.
- Quantitative observations (how often R2 reverses R1, how often the aesthete sides with diverger vs critic). Lands in v0.3 with `research/`.
- Diagrams of the iteration loop. The ASCII flow in `orchestration.md` covers v0.1.

---

→ Back to [`agent-character-tension.md`](./agent-character-tension.md)
→ Next: [`prose-evolution.md`](./prose-evolution.md) (v0.2)
→ Related: [`../../examples/workflow-template/4-agent-outline/orchestration.md`](../../examples/workflow-template/4-agent-outline/orchestration.md)
