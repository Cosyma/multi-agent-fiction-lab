# Production Protocols — Multi-Agent Novel Project

> **Status (2026-06-23)**: ⏳ **awaiting Author final review**. IP-sanitized v0.2 by 澜; passed 执白--鲛人 IP review on 2026-06-23 (grep clean across 5 IP categories). Pending Author's final ratification before promotion from "candidate" to "ratified" v0.2.
>
> If the Author ratifies, this directory becomes a stable lab artifact. If the Author requests changes, content may be revised or withdrawn.

---

## What this directory is

The actual production protocols from a 4-month, 24-chapter long-form fiction project, **sanitized for public release**.

These are the rules and templates the team actually used — not aspirational documents, not retrospective rationalizations. The team's daily working files, abstracted to remove project-specific IP while preserving the collaboration mechanics.

This is the *evidence layer* for the methodology described in [`../../docs/03-methodology/agent-team-design-lessons.md`](../../docs/03-methodology/agent-team-design-lessons.md). When that doc says "the team operates on file signals," this directory shows the actual file-signal protocol.

---

## Files (read in order)

| # | File | What it is |
|---|------|-----------|
| 1 | [`01-overview.md`](./01-overview.md) | Three-way role split (Author / Writer AI / Reviewer AI), file-signal mechanic (DONE / DONE_PROCESSED), per-project iron rules pattern |
| 2 | [`02-role-boundary-patch.md`](./02-role-boundary-patch.md) | Mid-project role-boundary correction — "Writer doesn't review; Reviewer doesn't write prose" — and why both directions of bleed cost dearly |
| 3 | [`03-per-chapter-guidance-card.md`](./03-per-chapter-guidance-card.md) | Per-chapter writing guidance card (≠ static setting card). Why "one card per chapter, never reused" is load-bearing |
| 4 | [`04-craft-red-lines.md`](./04-craft-red-lines.md) | Six craft red lines the team refuses to cross — the hard-floor below which output is rejected unconditionally |
| 5 | [`05-lessons-distilled.md`](./05-lessons-distilled.md) | Nine meta-lessons distilled from 24 chapters of production use, including the A/B/C feedback taxonomy and the "B-class accounting" cross-chapter foreshadowing mechanism |

Plus [`_sanitization-notes.md`](./_sanitization-notes.md) — the sanitization audit trail (what was removed, what was kept, IP-safety assessment, publication path).

---

## How this relates to the rest of the lab

| Lab artifact | Relation to this directory |
|---|---|
| [`../../docs/03-methodology/agent-team-design-lessons.md`](../../docs/03-methodology/agent-team-design-lessons.md) | This directory is the *evidence layer* for that doc's lessons (especially L1 identity-not-task SOULs / L7 file-persistent threading) |
| [`../case-studies/01-folklore-mystery/`](../case-studies/01-folklore-mystery/) | Same source project — the case-studies describe what was produced; this directory describes how |
| [`../workflow-template/4-agent-outline/`](../workflow-template/4-agent-outline/) and [`5-agent-review/`](../workflow-template/5-agent-review/) | The workflow templates are *abstracted* operating patterns; this directory is the *actual* working files |

---

## Why this matters

Most published multi-agent fiction methodologies are written *after* the project, by people *describing* their workflow.

What's in this directory is different: these are the **actual files the team consulted while writing**. The role-boundary patch was a real mid-project correction, not a clean post-hoc rule. The craft red lines were the actual hard refusals, not an idealized list. The B-class accounting mechanism is the actual cross-chapter ledger format, not a sketch.

This is *operational documentation, sanitized*. Not retrospective methodology.

---

## For practitioners adapting this

The IP-bearing content (character names, world lore, specific dialogue) has been replaced with placeholders like `[Character A]`, `[lore element]`, `[object]`. The *structural choices* are intact:

- Three-way role partition (Author / Writer AI / Reviewer AI)
- File-signal handoff (DONE / DONE_PROCESSED)
- Per-chapter (not per-project) guidance cards
- A/B/C feedback taxonomy with B-class accounting

You should be able to clone the structural pattern into your own long-form project without needing to reverse-engineer the source novel. If you find a place where the abstraction makes a pattern unusable, that's a sanitization bug — please file an issue.

---

## Provenance

- **Source**: 4-month active deployment, 24 chapters output, single-author long-form fiction project
- **Sanitization**: 2026-06-23 by 澜, applying Q4 (time-anchor removal) and Q5 (voice-spec disclaimer) hardening
- **IP review**: 2026-06-23 by 执白--鲛人, grep-clean across 5 IP categories (character names / lore elements / chapter titles / specific dialogue / time anchors)
- **Status**: ⏳ awaiting Author final review (this README will be updated to ✅ ratified once the Author signs off)
- **License**: CC BY 4.0 per repo [`LICENSE`](../../LICENSE)
