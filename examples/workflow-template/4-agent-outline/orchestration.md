# 4-Agent Outline Discussion — Orchestration

Two-round debate + final ruling. Clone-able skeleton.

---

## Inputs (you provide)

- `00_输入包.md` — input package (see [`docs/02-architecture.md`](../../../docs/02-architecture.md))
- 4 agents with SOULs loaded (see [`SOUL-template.md`](./SOUL-template.md))

## Outputs (generated)

```
session_dir/
├── 00_输入包.md
├── 01_diverger.md         # R1
├── 02_critic_r1.md        # R1
├── 03_aesthete_r1.md      # R1
├── 04_critic_r2.md        # R2 vs diverger
├── 05_aesthete_r2.md      # R2 arbitration
├── 06_summary.md          # Captain synthesis
└── 07_decision.md         # Captain ruling (promote-able)
```

## Flow

```
ROUND 1 — Independent (agents do NOT see each other)
─────────────────────────────────────────────────────
diverger   ─┐
critic     ─┼─→ each gets only INPUT_CONTENT
aesthete   ─┘

ROUND 2 — Cross-challenge (agents see selected R1 outputs)
─────────────────────────────────────────────────────────
critic     ─→ INPUT + diverger_R1
                → critic_R2 (specific challenges to diverger)

aesthete   ─→ INPUT + diverger_R1 + critic_R1 + critic_R2
                → aesthete_R2 (arbitration)

FINAL — Captain ruling
──────────────────────
captain    ─→ ALL above
                → 06_summary.md + 07_decision.md
```

## Why this shape

**Why R1 independent**: prevents groupthink. Three independent first-pass opinions form the diagonal surface for R2 to work on.

**Why critic challenges diverger specifically**: critic's job is to find breaks, not to opine in general. Targeted R2 is more useful than a second pass of R1.

**Why aesthete arbitrates, not captain**: aesthete is taste-forward and operates at the same content layer. Captain shouldn't decide quality, only consolidate. Splitting "what's good" from "what wins" prevents synthesis bias.

**Why captain produces two files**: summary captures the journey (useful for future sessions / author retrospective); decision is the only file that goes downstream. Keeping them separate prevents the ruling from being diluted by deliberation traces.

## Implementation skeleton (orchestrator-agnostic)

```python
# Pseudocode — adapt to your orchestrator (OpenClaw, LangGraph, AutoGen, CrewAI, OpenAI Swarm...)

def run_session(input_path, session_dir):
    INPUT = read(input_path)

    # Round 1 — parallel, independent
    diverger_r1 = call_agent("diverger", INPUT)
    critic_r1   = call_agent("critic", INPUT)
    aesthete_r1 = call_agent("aesthete", INPUT)
    save_all([diverger_r1, critic_r1, aesthete_r1], to=session_dir)

    # Round 2 — sequential, with R1 context
    critic_r2 = call_agent(
        "critic",
        INPUT + "\n\n## diverger Round 1\n" + diverger_r1,
        instruction="Challenge diverger's proposals specifically."
    )
    aesthete_r2 = call_agent(
        "aesthete",
        INPUT
        + "\n\n## diverger R1\n" + diverger_r1
        + "\n\n## critic R1\n" + critic_r1
        + "\n\n## critic R2\n" + critic_r2,
        instruction="Arbitrate aesthetic value between proposals and critiques."
    )
    save_all([critic_r2, aesthete_r2], to=session_dir)

    # Final — captain
    captain_out = call_agent(
        "captain",
        INPUT
        + "\n\n## All R1\n" + diverger_r1 + critic_r1 + aesthete_r1
        + "\n\n## All R2\n" + critic_r2 + aesthete_r2,
        instruction="Consolidate. Produce summary + decision."
    )
    save_summary_and_decision(captain_out, to=session_dir)
```

## Common pitfalls

1. **Skipping R1 independence** → groupthink; R2 has nothing to work on
2. **Letting captain introduce new content** → ruling becomes another opinion instead of synthesis
3. **Averaging instead of ruling** → "both proposals have merit" is failure, not diplomacy
4. **Reusing critic across rounds without role-shift** → R1 critic and R2 critic produce different shapes of output; the prompt must be different
5. **Forgetting to save raw stdout** → if the ruling looks weird, you need the captain's full trace to debug

## Adapting to your domain

The 4-agent shape (diverge / critique / arbitrate / rule) generalizes beyond fiction. Tested mental models:

| Domain | diverger | critic | aesthete | captain |
|--------|----------|--------|----------|---------|
| Fiction outline (this lab) | structural alternatives | logic breaks | taste arbitration | ruling |
| Product PRD review | feature alternatives | requirements breaks | user-value arbitration | go/no-go |
| Research proposal | hypothesis alternatives | methodology gaps | significance arbitration | next-step |
| Strategy memo | option alternatives | execution risks | strategic fit arbitration | decision |

The pattern transfers. The SOUL specifics need re-tuning per domain.

---

→ Back to [README](../../../README.md)
→ Next: [5-agent review template](../5-agent-review/) (v0.2)
