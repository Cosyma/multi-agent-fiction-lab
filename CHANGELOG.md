# Changelog

All notable changes to this project are documented here.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html) — though pre-1.0 versioning here reflects **audience-readiness milestones** rather than feature backlogs (see [`docs/05-roadmap.md`](./docs/05-roadmap.md)).

---

## [Unreleased]

### To land in v0.3 (target 2026-08)
- Full case-study excerpt text in `case-鲛人蛇吻.md` + `case-旁证体.md` (D14 silent-ratified 2026-06-19; pending sanitization coordination 执白 + 澜)
- `复盘-旁证体.md` (craft methodology long-form, by 执白--旁证体)
- `research/01-problem-statement.md` + `research/02-evaluation-metrics.md` skeletons
- Methodology docs case-walkthrough expansion

## [0.2.0-candidate] — 2026-06-23

> Multi-agent-practitioner-ready milestone. Marked *candidate* until Author signs off on `examples/protocols-from-novel-project/` content (sanitization is IP-reviewed but Author final review pending).

### Added
- `examples/protocols-from-novel-project/` — 5 production protocols (sanitized) + README + sanitization audit trail. v0.2 by 澜, IP-reviewed by 执白--鲛人 2026-06-23. The actual files the team consulted while writing 24 chapters; not retrospective methodology.
- `docs/03-methodology/agent-team-design-lessons.md` v0.2 research-framing layer integrated from 澜's snippet draft (Mason & Mitroff / Thompson / Sunstein-Thaler / Lave-Wenger / Vygotsky / Hassenzahl / Csikszentmihalyi / Deci-Ryan). L3 + L9 promoted to H1-H3 hypothesis form. L2 + L8 marked working-note / operating-discipline. L10 carries n=1 caveat. New "Cross-lesson connections" section identifies L1+L5+L6 as a paper triplet.

### Changed
- `examples/case-studies/01-folklore-mystery/case-鲛人蛇吻.md` — status header updated to reflect D14 silent-ratification (2026-06-19)
- `examples/case-studies/01-folklore-mystery/case-旁证体.md` — same as above

### Decisions executed
- D14 silent-ratification reached its 2026-06-19 deadline with no objections from 执白--鲛人 or 执白--旁证体; excerpts-mode publication is now the default

### Notes
- The "candidate" tag on v0.2 will be removed when the Author ratifies the `protocols-from-novel-project/` content explicitly
- `agent-team-design-lessons.md` source framing draft: `0-growup-lan/research-portfolio/snippets/agent-team-lessons-framing-v0.1.md` (澜, 2026-06-17)

## [0.1.0] — 2026-06-12

### Added — methodology
- `docs/01-why.md` — market gap + this lab's position
- `docs/02-architecture.md` — two agent teams + input package + orchestration
- `docs/03-methodology/agent-memory.md` — memory-as-workflow design (no vector DB)
- `docs/03-methodology/agent-consistency.md` — three drift modes + three mechanisms
- `docs/03-methodology/agent-character-tension.md` — paired-character design pattern (craft gatekeeper × ethical calibrator)
- `docs/03-methodology/outline-evolution.md` (skeleton) — outline iteration pattern (R1 / R2 / captain)
- `docs/03-methodology/prose-evolution.md` (skeleton) — prose iteration with rhythm-gate
- `docs/04-genre-adaptation.md` (skeleton) — cross-genre adaptation logic
- `docs/05-roadmap.md` — audience-readiness milestones

### Added — workflow templates
- `examples/workflow-template/4-agent-outline/SOUL-template.md` — placeholder personae for diverger / critic / aesthete / captain
- `examples/workflow-template/4-agent-outline/orchestration.md` — R1 / R2 / arbitration / ruling flow
- `examples/workflow-template/5-agent-review/SOUL-template.md` — placeholder personae for rhythm / blocking / voice / forbidden / captain
- `examples/workflow-template/5-agent-review/orchestration.md` — gate + parallel + cleanup + consolidate flow

### Added — case studies
- `examples/case-studies/01-folklore-mystery/case-鲛人蛇吻.md` (skeleton) — workflow validation case
- `examples/case-studies/01-folklore-mystery/case-旁证体.md` (skeleton) — craft baseline case

### Added — infrastructure
- `LICENSE` — MIT (code) + CC BY 4.0 (docs) + rights-reserved (source novels)
- `CITATION.cff` — CHI / arxiv friendly citation metadata
- `DECISIONS.md` — 15 logged design decisions with rationale
- `STATUS.md` — live status dashboard
- `CHANGELOG.md` — this file
- `CONTRIBUTING.md` — contribution policy
- `.gitignore` — macOS / IDE / language artifact filtering

### Added — distribution drafts
- `distribution/linkedin-en.md` (publish target: v0.5) — LinkedIn EN article, 300–500 words
- `distribution/zhihu-zh.md` (publish target: v0.5) — 知乎 ZH long-form, 1500–2500 chars

### Decisions logged
- D01–D11: foundational decisions (positioning, naming, audience layering, scope guards, phasing, workflow abstraction, model selection, case ordering, license, genre buckets, citation)
- D12: paper venue — CHI primary + arxiv preprint backup, 7 evaluation metrics
- D13: framework comparison — LangGraph + AutoGen + CrewAI + OpenClaw (self-built); no Swarm, no MetaGPT
- D14: source novel publication — excerpts + collaboration request (silent-ratification by 2026-06-19)
- D15: build priority — portfolio first, research follows

---

> Earlier exploration (pre-v0.1) is logged in development notes (`STATUS.md` recent history section).
