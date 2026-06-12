# Prose Evolution: How a Draft Iterates From First Pass to Final

> Status: **v0.1 skeleton** · expanded in v0.2 with a chapter-level walkthrough.

After the outline iteration converges (see [`outline-evolution.md`](./outline-evolution.md)), the prose itself goes through a parallel but **structurally different** iteration. The 5-agent prose-review team — rhythm, blocking, voice, forbidden, captain — audits each draft pass. The author rewrites based on the ruling. The pattern repeats per chapter.

---

## What prose iteration is not

Same caveat as `outline-evolution`: this is not "the author writes v1, v2, v3." Each version emerges from a structured review against specialized agents.

But unlike outline iteration (which is **parallel debate**), prose iteration is **sequential gating with parallel sub-audits**.

## The five-stage pattern

| Stage | Role | What it gates on |
|-------|------|------------------|
| 1. **rhythm-check** (gate first) | Sees if the chapter's engine is intact — opening, mid-section, closing | If engine broken → **STOP**. Fix structure before continuing. |
| 2. **blocking-check** + **voice-check** (parallel) | Are positions / movements clear? Are characters' voices distinct? | Independent dimensions. Run together to save round-trips. |
| 3. **forbidden-check** | Author intrusions, over-explanation, default LLM contrast clauses ("不是 X 是 X") | Late-stage cleanup — once structure is OK, scrub for prose tics. |
| 4. **review-captain** (consolidate) | Reads all 4 outputs. Merges overlapping findings. Orders fixes by priority. | Produces a single fix-list, not a list-of-lists. |
| 5. **Author rewrites** | Takes captain's ruling. Decides apply / defer / reject. Rewrites. | Repeat from stage 1 until clean. |

## Why rhythm-check is the gate

Long-form prose has structural failure modes that **no amount of sentence polish fixes**. If a chapter's opening doesn't earn its place, no voice work matters. The rhythm-check gate is what stops the author from spending three hours polishing a chapter that should be cut or restarted.

This is also what separates prose review from copy-editing. A copy-editor catches sentences. **A rhythm gate catches whole chapters.**

## Why blocking + voice in parallel

These are **independent dimensions**. A staging error (who's standing where) and a voice drift (a character starts sounding like the author) don't interact. Running them as separate calls saves time without cross-pollination risk.

## Why forbidden-check is last

Forbidden patterns are surface artifacts. They show up *after* structure and voice are right. Running forbidden-check first wastes its capacity — most patterns it would flag are about to be rewritten anyway as the structure changes.

## Why review-captain consolidates

Without consolidation, the author gets 4 separate fix-lists. Half of them overlap. Ordering becomes a task. Captain takes that task off the author's plate — and the author reads **one ordered list, not four**.

## What "iteration" produces (across multiple passes per chapter)

A chapter typically goes through **2–4 review passes** before reaching a stable form. Each pass:

- Locks in some changes
- Surfaces new tensions (often from the changes themselves)
- Continues until the captain reports *"low-severity-only this round"*

By pass 3–4, the chapter is publish-ready by the lab's standards. The author still does a final read; the review team **does not replace** author oversight — it structures the audit.

## What kept this from being mechanical

Same as outline-evolution: pattern provides the structure, judgment provides the substance.

In particular: **the rhythm gate is the most judgment-intensive call**. A chapter can pass blocking + voice + forbidden and still die at rhythm. When that happens, the author must decide whether to rewrite the chapter or accept that this chapter's engine is intentionally quiet (some chapters are).

## Why this matters for the lab's argument

Both the outline iteration (parallel debate) and the prose iteration (sequential gating) are workflow patterns the lab claims are more honest about long-form writing than a generic "agent reviews then revises" loop. The outline team handles **structural commitment under disagreement**; the prose team handles **layered surface validation**. Different problems → different patterns. This is what *"two cooperating agent teams"* means in practice.

## What this v0.1 skeleton does NOT include

- A walkthrough of an actual chapter review session. Lands in v0.2 with case material.
- The full SOUL templates for the 5 review agents — placeholder in v0.1 (`examples/workflow-template/5-agent-review/README.md`), fills in v0.2.
- Quantitative observations (how often rhythm-check forces a STOP, how often the captain's ruling matches author intuition). Lands in v0.3 with `research/`.

---

→ Back to [`outline-evolution.md`](./outline-evolution.md)
→ Related: [`../../examples/workflow-template/5-agent-review/`](../../examples/workflow-template/5-agent-review/) (v0.2 placeholder for the SOUL templates)
→ Related: [`agent-consistency.md`](./agent-consistency.md) (the metrics rhythm-check + voice-check gate against)
