# Empirical Evidence: 4-Agent Personality Difference on the Same Task

> **Source**: 4-agent outline-discussion session, 2026-03-11. Task: chapter-level outline v2 for Volume 1 of an ongoing novel project.
> **Excerpt policy**: per [`DECISIONS.md`](../../../DECISIONS.md) D14 — sanitized excerpts ≤ 3,000 chars total. This file ≈ 2,200 chars of agent output.
> **Sanitization**: character names → `[Character A/B/C]`; story-specific concepts → bureaucratic placeholders (`[credential]`, `[shared interface]`, `[processed-out]` etc.). Preserves voice / structure / posture (the evidence dimensions); abstracts the IP-bearing story content.
> **Why this file is in the repo**: empirical support for the *"model personality is real, persistent, asymmetric"* claim that anchors [`../../../docs/03-methodology/agent-memory.md`](../../../docs/03-methodology/agent-memory.md) "Model selection as memory" and [`DECISIONS.md`](../../../DECISIONS.md) D07 (model selection as criteria, not conclusion).

---

## The setup

Same input package → 3 specialized agents (each running a different model) → 3 visibly different responses.

- **diverger** runs on `qwen3-max`, bound to *"propose new structural alternatives"*
- **critic** runs on `glm-4.7`, bound to *"find logic / causality / motivation gaps"*
- **aesthete** runs on `kimi-k2.5`, bound to *"judge aesthetic + reading feel"*

All three got the **same** ~3,000-token input package. All three were instructed to follow a **strict 7-section output format**. The output format alone does not constrain *how* they think — and how they think diverges visibly.

---

## §1 — Sanitized excerpts: each agent's "recommended scene"

### diverger (qwen3-max) — wide imagery, multi-thread weaving

> The "[deduction] of [Character C]" should happen at the edge of [Character A]'s own [credential] failing — not while he reasons calmly in an archive, but as he attempts, through some [shared bureaucratic interface], to retrieve [Character C]'s [profile], when the system begins reassessing his own [credential]'s risk grade as "anomalous access." Under that embodied pressure of "I too am being [processed out]," [Character A] notices the gap between [Character C]'s last-known relationship link time and the system-recorded "final version" — a 48-hour gap. That gap hides [Character C]. The tension: [Character A] is not investigating a case, he is using his own [processed-out] progress as a reference frame to read another person's [processed-out] progress — while [Character B] is watching from the other end of the [shared interface], deciding whether to intervene.

**What this output shows about qwen3-max's axis**: builds out scenes via *concentric imagery* — multiple narrative threads woven into a single moment ([Character A]'s peril + [Character C]'s mystery + [Character B]'s witness). Vivid, generative, breadth-first. Hard to redirect once launched.

---

### critic (glm-4.7) — structural-gap pointing, sharp causality

> The chapter-division table currently lacks a "per-chapter weight distribution across the three engines" — especially [Character A]'s private engine startup-marker at Ch.00-03 and progress-marker at Ch.07-10. This makes the main-line progress potentially complete at the case-surface level but hollow at the thematic level.

> Against writing the "[deduction] of [Character C]" as pure technical derivation ([Character A] queries data, runs comparison, draws conclusion), leaving the node serving only the case function — if the "[Character C] discovery" doesn't trigger [Character A]'s cognitive upgrade about his own [processed-out] progress ("[Character C] is the previous me / the next me"), then the private engine in Volume 1 is dead, and the triple-engine system runs on only two.

**What this output shows about glm-4.7's axis**: structural surgeon — diagnoses what's *missing* at the architectural level, then traces the specific causality break it would create. Sharp, gap-oriented, refusal to accept smooth surface. Holds disagreement under pressure.

---

### aesthete (kimi-k2.5) — reading-feel concern, craft-first

> If the Ch.00-15 division becomes a mechanical assignment of "case-task / world-task / relationship-task" per chapter, every chapter will read like ticking off KPIs, not like a person doing one specific thing in a world that is currently being [processed].

> Against writing Ch.00-03 as "world-explanation chapters" — first introduce [Character A], then [Character B], then [Bureau Y], then the case. This rotating-debut writing makes the first three chapters read like a character-introduction PowerPoint, not *"this city is being [processed], and [Character A] is the thread that wasn't [processed in]."*

**What this output shows about kimi-k2.5's axis**: concerned with how each chapter *feels* to read, not whether it checks boxes. Refuses the "completion-driven" frame. Holds aesthetic judgment without becoming defensive when challenged later.

---

## §2 — What this evidence supports

The three excerpts above show, on **the same input**, with **the same output-format constraint**:

| Axis | qwen3-max | glm-4.7 | kimi-k2.5 |
|------|-----------|---------|-----------|
| **Length tendency** | Long, concentric | Mid, structurally-organized | Mid, numbered-points |
| **Posture** | Generative / proposing | Diagnostic / refusing | Reading-experience guarding |
| **Failure mode if misassigned** | If used as critic: would still generate, not refute. If used as aesthete: would over-propose. | If used as diverger: would refuse rather than propose. If used as aesthete: would still diagnose. | If used as critic: would soft-pedal. If used as diverger: would refuse mechanical generation. |

**This is what we mean by *"model personality is real, persistent, and asymmetric."*** None of these axes are prompt-tunable into another model's space. We can sharpen qwen3-max with prompt; we cannot make it glm-4.7.

---

## §3 — Methodological note

These three excerpts were captured under production conditions for an ongoing creative project (one of the lab's case-study novels). Per the lab's data-availability policy (see [`DECISIONS.md`](../../../DECISIONS.md) D14), sanitized excerpts are released here; full session data is available via collaboration request.

The sanitization preserves voice / structure / posture (the dimensions this excerpt is evidence for) while abstracting story-specific content (character names, world-specific bureaucratic concepts) to placeholders. The pattern visible above is **reproducible across the lab's session archive** (n > 30 sessions over 9 months).

---

→ Related: [`SOUL-template.md`](./SOUL-template.md) (the agent personae these models were running) · [`orchestration.md`](./orchestration.md) (the workflow that produced this output) · [`../../../docs/03-methodology/agent-memory.md`](../../../docs/03-methodology/agent-memory.md) "Model selection as memory"

*Sanitization completed 2026-06-12. Released under CC BY 4.0 per [`LICENSE`](../../../LICENSE).*
