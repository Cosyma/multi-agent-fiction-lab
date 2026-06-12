# multi-agent-fiction-lab

[![Status](https://img.shields.io/badge/status-active-brightgreen)](.) [![Genres](https://img.shields.io/badge/genres-1%20live-blue)](.) [![v0.1](https://img.shields.io/badge/version-0.1-orange)](.) [![License](https://img.shields.io/badge/license-MIT%20%2B%20CC%20BY%204.0-yellow)](./LICENSE)

[![Last Commit](https://img.shields.io/github/last-commit/Cosyma/multi-agent-fiction-lab)](https://github.com/Cosyma/multi-agent-fiction-lab/commits/main) [![Commit Activity](https://img.shields.io/github/commit-activity/m/Cosyma/multi-agent-fiction-lab)](https://github.com/Cosyma/multi-agent-fiction-lab/commits/main) [![Stars](https://img.shields.io/github/stars/Cosyma/multi-agent-fiction-lab?style=social)](https://github.com/Cosyma/multi-agent-fiction-lab/stargazers)

> A PM-driven lab for multi-agent collaborative long-form fiction.
>
> Not a writing tool. A working methodology — designed, validated, and documented by someone who builds AI agent platforms by day and writes novels by night.

**Live**: folklore-mystery genre, 2 novels (100k+ words combined)
**Coming**: mystery (本格 / 社会派) + psychological-character-study

## The workflow shape

```
              AUTHOR (you)
              /         \
           brief        draft
             │           │
             ▼           ▼
       ┌──────────┐ ┌──────────┐
       │ 4-AGENT  │ │ 5-AGENT  │
       │ OUTLINE  │ │ PROSE    │
       │  DEBATE  │ │  REVIEW  │
       └────┬─────┘ └────┬─────┘
            │            │
         ruling      fix list
            │            │
            └─→ AUTHOR ←─┘
                decides
```

Two cooperating agent teams. The author is the messenger and the final decider. **No autonomous runtime · everything is auditable markdown.**

→ Full architecture in [`docs/02-architecture.md`](./docs/02-architecture.md)

---

## Why this lab exists

Most AI fiction tools are built by engineers for writers. **This is built by a writer working as a PM on their own workflow.**

The gap that matters:

- AI writing tools treat consistency, memory, and voice as **infrastructure problems** (vector DB, RAG, fine-tuning)
- This lab treats them as **workflow problems** (multi-agent debate, persistent SOULs, shared input packages, model-task matching)
- The difference is who you let make the call — and how the call gets reviewed

→ Full motivation in [`docs/01-why.md`](./docs/01-why.md)

## What's inside

```
multi-agent-fiction-lab/
├── docs/                                Methodology + architecture
│   ├── 01-why.md
│   ├── 02-architecture.md
│   └── 03-methodology/
│       └── agent-memory.md (v0.1)
├── examples/
│   ├── workflow-template/               Clone & run
│   │   ├── 4-agent-outline/             diverger / critic / aesthete / captain
│   │   └── 5-agent-review/              rhythm / blocking / voice / forbidden / captain (v0.2)
│   └── case-studies/
│       ├── 01-folklore-mystery/         (excerpt + intent — WIP)
│       └── 02-mystery/                  (planned)
├── research/                            Evaluation + framework comparison (v0.2+)
├── CITATION.cff
└── LICENSE                              CC BY 4.0 (docs) + MIT (code)
```

## Three doors in

| If you are... | Start here | Time |
|--------------|-----------|------|
| **PM hiring manager** | [`docs/01-why.md`](./docs/01-why.md) + [`docs/02-architecture.md`](./docs/02-architecture.md) | 60s |
| **Multi-agent practitioner** | [`examples/workflow-template/4-agent-outline/`](./examples/workflow-template/4-agent-outline/) | 10min |
| **Researcher** | `research/` (v0.2+) | 40min |

## What makes this not generic

- **Two agent teams that talk to each other** — 4-agent outline debate (R1 independent → R2 cross-challenge → arbitration → ruling) + 5-agent prose review (rhythm / blocking / voice / forbidden / captain consolidation)
- **Memory as workflow, not infrastructure** — persistent SOULs in workspace, briefing dossier auto-included, input packages per session — no vector DB tricks
- **Model selection as craft** — qwen3-max for divergence (broad surface), glm-4.7 for criticism (sharp), kimi-k2.5 for aesthetics (taste), gemini-2.5-flash for forbidden patterns (fast pattern match), claude-sonnet for arbitration (synthesis). Each model picked for its cognitive flavor, not benchmark score.

→ Architecture details in [`docs/02-architecture.md`](./docs/02-architecture.md)

## Reproduce

```bash
git clone https://github.com/{TBD}/multi-agent-fiction-lab.git
cd multi-agent-fiction-lab/examples/workflow-template/4-agent-outline
# Fill SOUL-template.md placeholders for your domain
# Run via orchestration.md (R1 → R2 → ruling)
```

You'll need: any multi-agent orchestrator (OpenClaw, LangGraph, AutoGen, CrewAI...) + API access to 3–4 LLMs with distinct cognitive flavors.

## Roadmap

- **v0.1** (current) — README + methodology core + 4-agent outline template + folklore-mystery skeleton
- v0.2 — 5-agent review template + 1 case study live + `research/` skeleton
- v0.3 — Framework comparison (vs LangGraph / AutoGen / CrewAI)
- v0.4+ — Genre adaptation guide + research paper draft

→ Full timeline with audience-readiness milestones and exit criteria: [`docs/05-roadmap.md`](./docs/05-roadmap.md)

## Decisions log

Every non-obvious design choice in this lab is recorded with rationale in [`DECISIONS.md`](./DECISIONS.md):

- Why this is a lab, not a tool (D01)
- Why three audiences in one repo (D03) ⭐
- Why two case studies are ordered (craft baseline → workflow validation, D08) ⭐
- Why model selection is written as a criterion, not a conclusion (D07)
- Pending: source-novel publication mode (D14), third genre bucket (D10)

Read `DECISIONS.md` when you want to know *"why this and not that."*

## Cite

```bibtex
@misc{kanglingyi_2026_multi_agent_fiction_lab,
  author = {Kang Lingyi},
  title  = {multi-agent-fiction-lab},
  year   = {2026},
  url    = {https://github.com/TBD/multi-agent-fiction-lab}
}
```

## Note

> "Portfolio 价值在'设计了这个工作流'，不在'这是咒语'——咒语公开反而稀释差异化。"
>
> *Portfolio value lies in "designing this workflow", not in "the spell" — publishing the spell dilutes the differentiation.*
>
> — Internal review, 2026-06-11

## Author

Kang Lingyi. PM building knowledge-driven AI agent platforms. Computational social science researcher in training.

---

*A lab is not a product. Nothing here is meant to be a finished service. It's a working methodology kept open — for the few people who'd find this exact intersection useful.*
