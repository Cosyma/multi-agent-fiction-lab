# Architecture

Two agent teams + a shared input pattern + an orchestration loop. That's the whole system.

---

## The two teams

```
                    ┌──────────────────────────────────┐
                    │   AUTHOR (康康)                   │
                    │   - Provides brief                │
                    │   - Reviews ruling                │
                    │   - Decides apply/defer/rewrite   │
                    └────────────┬──────────────────────┘
                                 │
        ┌────────────────────────┼────────────────────────┐
        │                                                 │
        ▼                                                 ▼
┌─────────────────────────┐                ┌─────────────────────────────┐
│ 4-AGENT OUTLINE TEAM     │                │ 5-AGENT PROSE REVIEW TEAM    │
│ (volume / chapter card) │                │ (chapter draft)              │
├─────────────────────────┤                ├─────────────────────────────┤
│ R1 independent:          │                │ Sequential:                  │
│   - diverger             │                │   - rhythm-check (gate)      │
│   - critic               │                │   - blocking + voice         │
│   - aesthete             │                │     (parallel)               │
│ R2 cross-challenge:      │                │   - forbidden-check          │
│   - critic vs diverger   │                │   - captain                  │
│   - aesthete arbitrates  │                │                              │
│ Final:                   │                │ Output:                      │
│   - captain rules        │                │   - Consolidated fix list    │
│                          │                │   - Priority order           │
└─────────────────────────┘                └─────────────────────────────┘
```

Both teams share the same input pattern (locked facts + author brief + dossier) and the same output ritual (a single ruling, not averaged opinions).

## The input package pattern

Every session, both teams, starts with `00_输入包.md`:

```
1. 固定事实源 (locked facts — never debated)
2. 角色 / 情感锚点 (locked behavior, e.g. CP design)
3. 项目速查手册 (auto-loaded briefing dossier — ~3000 words condensed)
4. 外部主笔输入 (author's brief for THIS session only)
5. 禁止改动 (explicit out-of-scope list)
6. 期望输出 (output format spec — 7 points for outline, custom for review)
```

This is **memory as workflow, not infrastructure**. No vector DB. No RAG over the whole codex. Just the right slice of facts at the right time.

→ Details in [`03-methodology/agent-memory.md`](./03-methodology/agent-memory.md)

## The orchestration loop

```
Author brief
    │
    ▼
Generate input package (auto-wrap + dossier inject)
    │
    ▼
Run agents (sequential or parallel as required by team)
    │
    ▼
Captain consolidates → single ruling
    │
    ▼
State file updated → waiting_user_review = true
    │
    ▼
Author approves → promote ruling to main project space
                + advance stage in state.json
```

Implemented via **OpenClaw** (a multi-agent orchestrator running Lima VM + Mac CLI). But the **pattern transfers** to LangGraph, AutoGen, CrewAI — see `examples/workflow-template/` for clone-and-adapt skeletons.

## Why two teams, not one

Outline-level concerns and prose-level concerns require **different cognitive flavors** at different temperatures:

- **Outline team** debates structure → divergence + criticism + taste. Two rounds (independent, then cross-challenge). Arbitration ends it.
- **Prose review team** audits a draft → rhythm gates first (if the engine is broken, stop). Then blocking + voice in parallel (independent dimensions). Forbidden patterns last (cleanup). Captain consolidates.

Merging them into one team would dilute both. **Specialization is the point.**

## Models and orchestration platform

| Component | Choice | Substitutable? |
|----------|--------|----------------|
| Outline diverger | qwen3-max | Yes — any "broad surface" LLM |
| Outline critic | glm-4.7 | Yes — any "sharp" LLM |
| Outline aesthete | kimi-k2.5 | Yes — any "taste-forward" LLM |
| Outline captain | gemini-2.5-flash | Yes — any "synthesis" LLM |
| Review rhythm | qwen3-max | Yes |
| Review blocking | glm-4.7 | Yes |
| Review voice | kimi-k2.5 | Yes |
| Review forbidden | gemini-2.5-flash | Yes — fast model preferred |
| Review captain | claude-sonnet-4-6 | Yes — synthesis quality matters most here |
| Orchestration | OpenClaw + Lima VM gateway | Yes — LangGraph / AutoGen / CrewAI all work |

The model assignments are **not random**. They're the result of running the system, watching where each model fails, and re-assigning until each role has a model that matches its cognitive demand. See `03-methodology/agent-memory.md` for the heuristics.

## What this is not

- Not a tool you install
- Not a runtime service
- Not a fine-tuned model

It's **a workflow architecture**. The runtime can be anything that supports multi-agent orchestration. The methodology — the role design, the input package pattern, the two-round debate — is what transfers.

→ [Methodology details](./03-methodology/agent-memory.md)
→ [Working templates](../examples/workflow-template/)
