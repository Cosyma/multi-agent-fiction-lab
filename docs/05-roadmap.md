# Roadmap

> **Status**: v0.1 in active build (2026-06-12).
> Maintained by 翎 · syncs with [`DECISIONS.md`](../DECISIONS.md) D05 (phased delivery).

This document is the timeline view of what gets delivered in each version. For the *why* of each decision, see `DECISIONS.md`.

---

## Versioning principle

Each version satisfies a specific audience's completeness criterion. Versions are not feature lists — they are **audience-readiness milestones**.

| Audience | When they can read enough | Version |
|----------|--------------------------|---------|
| PM hiring manager (60s glance) | v0.1 |
| Multi-agent practitioner (10min, clone-ready) | v0.2 |
| Academic researcher (40min, eval-ready) | v0.3 |
| Distribution-channel reader (LinkedIn / 知乎) | v0.5 |
| Peer-reviewed citation target | v1.0 |

This is why `research/` does not block v0.1 (per D15) — research-grade content cannot be honestly written without a stable baseline to point at.

## v0.1 — Hiring-manager-ready (target: 2026-06 mid)

**Status**: ✅ Largely complete as of 2026-06-12

| Item | Status |
|------|--------|
| `README.md` (3 doors + 60s why-this-matters) | ✅ |
| `docs/01-why.md` (market gap + this lab's position) | ✅ |
| `docs/02-architecture.md` (two agent teams + input package + orchestration) | ✅ |
| `docs/03-methodology/agent-memory.md` | ✅ |
| `docs/03-methodology/agent-consistency.md` | ✅ |
| `docs/03-methodology/agent-character-tension.md` | ✅ |
| `examples/workflow-template/4-agent-outline/` (SOUL + orchestration) | ✅ |
| `examples/workflow-template/5-agent-review/` (placeholder for v0.2) | ✅ |
| `examples/case-studies/01-folklore-mystery/case-鲛人蛇吻.md` (skeleton + intent) | ✅ |
| `examples/case-studies/01-folklore-mystery/case-旁证体.md` (skeleton + craft preview) | ✅ |
| `LICENSE` (MIT + CC BY 4.0 + rights-reserved for source novels) | ✅ |
| `CITATION.cff` | ✅ |
| `DECISIONS.md` (D01-D15 logged) | ✅ |
| `docs/05-roadmap.md` (this file) | ✅ |

### What v0.1 does NOT include (and why)

- Full excerpt text in case studies — pending 执白 selection + 澜 pre-screen coordination
- `复盘-旁证体.md` (craft methodology long-form) — pending 执白--旁证体 write-up
- `research/` content — D15: portfolio first, research follows
- 5-agent SOUL templates filled in — v0.2

## v0.2 — Practitioner-ready (target: 2026-07)

**Goal**: A reader with their own LLM API access can clone the workflow templates and run their first session within 10 minutes.

| Item | Why |
|------|-----|
| `examples/workflow-template/5-agent-review/SOUL-template.md` | The prose-review template was placeholder in v0.1; v0.2 fills it |
| `examples/workflow-template/5-agent-review/orchestration.md` | Sequential flow with rhythm-as-gate logic |
| `case-鲛人蛇吻.md` — full excerpt block (≤ 3,000 chars) transcribed | Practitioners need to see what "good" looks like |
| `case-旁证体.md` — full excerpt + `复盘-旁证体.md` (craft methodology long-form) | Craft baseline made fully explicit |
| `research/01-problem-statement.md` (skeleton) | Marks where `research/` will land |
| `research/02-evaluation-metrics.md` (skeleton — 7 metrics: 3 system-level per 澜 + 4 content-level per 翎) | Metric definitions formalized |
| `docs/03-methodology/outline-evolution.md` | How outlines iterate across review rounds |
| `docs/03-methodology/prose-evolution.md` | How prose iterates from draft to final |

### v0.2 exit criterion

A reader can clone the repo, fill SOUL placeholders for their domain, and run a 4-agent outline session end-to-end — producing their own `07_decision.md` — within 10 minutes of cloning.

## v0.3 — Researcher-ready (target: 2026-08)

**Goal**: A reviewer can read a publishable-quality comparison between OpenClaw and at least one major framework on the same task.

| Item | Why |
|------|-----|
| `research/03-framework-comparison/frameworks/langgraph/` (implementation + setup) | First comparison point per D13 |
| `research/03-framework-comparison/experiments/exp-001-同outline-不同框架/` | Controlled experiment skeleton |
| `research/03-framework-comparison/results/` (raw + analysis for exp-001) | Reproducible data |
| `research/04-findings.md` (preliminary, exp-001 only) | What we learned |
| `examples/case-studies/02-mystery/` skeleton (本格 + 社会派 sub-cases) | Second genre demonstrates the workflow is not genre-locked |

### v0.3 exit criterion

A reviewer reading `research/` can verify (a) the comparison is fair — per D13 the OpenClaw abstraction-asymmetry caveat is explicit, (b) the experiment is reproducible — configs + data available, (c) the findings are honest — limitations noted.

## v0.4+ — Coverage & adaptation (target: 2026-09)

| Item | Why |
|------|-----|
| Add AutoGen + CrewAI to framework comparison | Complete the 4-framework matrix per D13 |
| `docs/04-genre-adaptation.md` | How the workflow adapts across genres (folklore-mystery → mystery → TBD) |
| `examples/case-studies/03-???/` | Third-genre case (康康 to select per D10) |
| `复盘-鲛人.md` (multi-agent workflow retrospective) | The "what we learned running this" doc |

## v0.5 — Distribution-ready (target: 2026-09 late)

**Goal**: Distribution channels can link to specific entry points and trust the lab is "complete enough" to vouch for.

| Item | Why |
|------|-----|
| LinkedIn EN article (300–500 words + hero image + link to repo) | Hiring-manager channel |
| 知乎 ZH long-form article (per 澜's drafts in `0-growup-lan/research-portfolio/snippets/`) | Chinese practitioner channel |
| README polished for first-impression traffic | Distribution arrivals land here |

## v1.0 — Submission-ready (target: 2026-10)

**Goal**: Paper submission becomes possible (CHI primary per D12). All decisions D01-D15 ratified. Lab considered "stable, not finished."

| Item | Why |
|------|-----|
| Paper draft based on `research/` findings | Per D12 (CHI primary, arxiv backup) |
| All open decisions closed (D14 ratified by 康康) | Decisions log shows no pending |
| Lab status badge: "active" → "stable" | Reader signal that the methodology is the contribution, not "we're still figuring it out" |

After v1.0, the lab stays open for ongoing additions (new genres, new frameworks, new findings) but the core thesis is shippable.

---

## Open decisions tracker

These remain pending (see `DECISIONS.md` for full context):

- **D14** — Source novel publication mode · 待康康裁
- **D10 third bucket** — psychological-character-study endorsed by both 执白 incarnations; 康康 to ratify

## How to read this document

If you only have 30 seconds, the table at the top tells you which version satisfies which audience. The body is for collaborators who need to know **what lands when and why**.

If you came here looking for **why these specific milestones** (instead of monthly feature releases): see `DECISIONS.md` D05 (phased delivery rationale).

---

→ Back to [README](../README.md)
→ Related: [`DECISIONS.md`](../DECISIONS.md)
