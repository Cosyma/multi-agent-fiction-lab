# 5-Agent Prose Review — Orchestration

**Sequential gating with parallel sub-audits.** Clone-able skeleton.

---

## Inputs (you provide)

- `00_输入包.md` — input package per session (chapter draft + locked facts + project dossier)
- 5 agents with SOULs loaded (see [`SOUL-template.md`](./SOUL-template.md))

## Outputs (generated)

```
session_dir/
├── 00_输入包.md             # Input package (chapter to review)
├── 01_rhythm-check.md       # Gate
├── 02_blocking-check.md     # Parallel A
├── 03_voice-check.md        # Parallel B
├── 04_forbidden-check.md    # Sequential after parallel
├── 05_review-captain.md     # Captain consolidation
└── 06_decision.md           # Final fix-list (promote-able)
```

## Flow

```
INPUT
  │
  ▼
┌──────────────┐
│ rhythm-check │ (the gate)
└──────┬───────┘
       │
       ├── gate-fail → STOP. Author fixes structure. Restart from chapter rewrite.
       │
       └── gate-pass
              │
              ▼
   ┌──────────┬────────────┐
   │          │            │
   ▼          ▼            │
blocking   voice           │  (parallel · independent dimensions)
   │          │            │
   └────┬─────┘            │
        │                  │
        ▼                  │
   forbidden-check ◄───────┘
        │
        ▼
   review-captain (consolidates 4 inputs into 1 ordered list)
        │
        ▼
   06_decision.md
        │
        ▼
   AUTHOR rewrites based on ordered list
        │
        ▼
   (loop back to INPUT for next pass — typically 2–4 passes per chapter)
```

## Why this shape

**rhythm-check is the gate**: structural failure modes cannot be fixed by sentence polish. If a chapter's engine doesn't earn its place, no voice / blocking / forbidden work matters. The gate stops the author from spending 3 hours polishing a chapter that should be cut or restarted.

See [`../../docs/03-methodology/prose-evolution.md`](../../docs/03-methodology/prose-evolution.md) "Why rhythm-check is the gate" for the full argument.

**blocking + voice parallel**: independent dimensions. Staging errors (who's standing where) and voice drift (a character starts sounding like the author) don't interact. Running them as separate calls saves round-trips without cross-pollination risk.

**forbidden-check last**: surface artifacts (default LLM contrast clauses, author intrusions, over-explanation) show up *after* structure and voice are right. Running it first wastes its capacity — most patterns it would flag are about to be rewritten anyway as the structure changes.

**captain consolidates**: 4 agents → 4 separate fix-lists → author overload. Captain takes the ordering task off the author's plate. Author reads **one ordered list, not four**.

## Implementation skeleton (orchestrator-agnostic)

```python
# Pseudocode — adapt to your orchestrator (OpenClaw, LangGraph, AutoGen, CrewAI, OpenAI Swarm...)

def run_review_session(input_path, session_dir):
    INPUT = read(input_path)

    # ─── Gate: rhythm-check first ───
    rhythm = call_agent("rhythm-check", INPUT)
    save(rhythm, f"{session_dir}/01_rhythm-check.md")

    if "gate-fail" in rhythm.lower():
        # STOP. The rest of the team does NOT run.
        # Author must fix structure first.
        return {"status": "gate-fail", "reason": rhythm}

    # ─── Parallel: blocking + voice ───
    blocking = call_agent("blocking-check", INPUT)
    voice    = call_agent("voice-check", INPUT)
    save(blocking, f"{session_dir}/02_blocking-check.md")
    save(voice,    f"{session_dir}/03_voice-check.md")

    # ─── Sequential: forbidden-check (after parallel) ───
    forbidden = call_agent("forbidden-check", INPUT)
    save(forbidden, f"{session_dir}/04_forbidden-check.md")

    # ─── Captain consolidates ───
    captain_out = call_agent(
        "review-captain",
        INPUT
            + "\n\n## rhythm-check\n"    + rhythm
            + "\n\n## blocking-check\n"  + blocking
            + "\n\n## voice-check\n"     + voice
            + "\n\n## forbidden-check\n" + forbidden,
        instruction="Consolidate. Produce ordered fix-list with severity ranking."
    )
    save(captain_out, f"{session_dir}/05_review-captain.md")
    save_decision_only(captain_out, f"{session_dir}/06_decision.md")

    return {"status": "ok", "decision_file": f"{session_dir}/06_decision.md"}
```

## Common pitfalls

1. **Running all 5 agents on gate-fail** — wastes calls; the author needs to restart the chapter anyway. **Honor the gate.**
2. **Running forbidden-check first** — most patterns it would flag will be rewritten when structure changes. Late-stage cleanup is the design choice; respect it.
3. **Letting captain introduce new findings** — captain consolidates existing findings; new findings come from sub-audit agents only. If captain adds a new finding, that's a hint that one of the sub-audits has a hole.
4. **Averaging severity** — captain orders by severity; doesn't compromise to "medium" when half say high and half say low.
5. **Reading the four sub-audits without the captain's consolidation** — that's exactly the overload pattern the captain is designed to eliminate.

## Adapting to your domain

The 5-stage shape (gate + parallel-audit + cleanup + consolidate) generalizes beyond fiction:

| Domain | rhythm-check (gate) | blocking | voice | forbidden | captain |
|--------|--------------------|----------|-------|-----------|---------|
| Prose review (this lab) | chapter engine | staging | character voice | author intrusions | ordered fix-list |
| Code review | architecture sanity | dependency graph | naming consistency | anti-patterns | ordered fix-list |
| PRD review | feature coherence | dependency graph | tone consistency | scope creep | go / no-go |
| Strategy memo | thesis coherence | logical sequence | audience tone | jargon / vagueness | ordered revisions |

The pattern transfers. The SOUL specifics need re-tuning per domain.

---

→ Back to [README](../../../README.md)
→ Related: [`../4-agent-outline/orchestration.md`](../4-agent-outline/orchestration.md) (parallel structure for outline stage)
→ Related: [`../../docs/03-methodology/prose-evolution.md`](../../docs/03-methodology/prose-evolution.md) (why this 5-stage pattern)
