# Agent Consistency: Holding Voice Across 100,000 Words

The hardest problem in long-form AI fiction is not generation. It's **consistency** — keeping a character recognizable, a plot causal, an aesthetic stable, across many chapters and many sessions. Here's how this lab approaches it.

---

## The three drift modes

Long-form fiction breaks in three predictable ways:

| Drift mode | Symptom | Where it surfaces |
|------------|---------|-------------------|
| **Voice drift** | A character starts speaking like the author's default register | Dialogue, internal narration |
| **Plot drift** | Events stop earning each other; coincidences accumulate | Causality between chapters |
| **Aesthetic drift** | The tone regresses toward LLM-mean (more polite, more explanatory, more symmetric) | Sentence-level texture |

All three failure modes share one cause: **the agent has access to "what was written before" but no commitment to "what makes it good"**.

Most AI-fiction tools try to solve drift with retrieval: better embeddings, longer context, more vector matches. This is necessary but insufficient. Retrieval gives the agent what came before. It does not tell the agent what to preserve.

## What this lab does instead

Treats consistency as a workflow problem with three explicit mechanisms:

### 1. Persistent SOULs (not per-call prompts)

Each agent in this lab has a `SOUL.md` in its workspace that survives across sessions. It encodes:

- **Negation up top** — what the agent does NOT do (prevents scope creep more reliably than positive instructions)
- **Single-sentence job** — the one thing the agent commits to
- **Bounded output format** — a hard cap on the surface area the agent can affect

A SOUL is not a prompt that gets refreshed each call. It is **a contract**. When you talk to the diverger agent on day 1 and day 100, you are talking to the same diverger — because the contract is the same.

This sounds obvious but is rare in practice. Most multi-agent systems reconstruct persona at every call, allowing slow drift in agent behavior. SOULs are tighter.

### 2. The "do not debate" list

Inside each session's input package (`00_输入包.md`) there is an explicit list of **facts that cannot be touched**: locked character behavior, fixed CP design, irreversible plot beats already committed to.

The agents are not allowed to propose alternatives to anything on this list.

This sounds restrictive. It is. It's also the entire reason long-form holds together. Without it, a divergent thinker will eventually propose burning down a character the author already committed to. Then the critic has to re-argue first principles every session. The "do not debate" list eliminates this entire failure mode.

**Consistency is not only what you remember. It's also what you refuse to re-litigate.**

### 3. A dedicated voice-check agent

In the 5-agent prose-review team, `voice-check` exists for one job: detect drift in character voice across chapters.

Its operating rule: **delete the character names from the dialogue and narration. Can you still tell who's speaking?**

If yes, voice is intact. If no, drift has begun — and the cause must be surfaced before continuing. Common causes:

- The character starts handling pressure with the author's default tone (pressure peaks invite voice collapse)
- System-role characters start talking like each other (role-differentiation lost)
- A philosopher character starts narrating thematic conclusions instead of acting within his role

voice-check returns position + diagnosis + minimum-fix direction. It does not rewrite. The author does the fix.

## The fidelity target: 旁证体's seven craft hooks

A consistency mechanism is only as good as the target it tries to preserve. This lab uses **旁证体** (see [`case-旁证体.md`](../../examples/case-studies/01-folklore-mystery/case-旁证体.md)) as the explicit fidelity target, with seven craft hooks the workflow must preserve:

1. **物件叙事链** — objects carry meaning, not interiority
2. **双对照** — three layers of mirror structure (object cross-witness / CP 冰火 contrast / arc reversal)
3. **B-line accounting** — what's actually happening beneath consciousness must surface through objects
4. **工艺红线** — restraint as gravity / no past-life explanation / HE-as-responsibility / etc.
5. **"不是 X 是 X" forbidden** — refuse the default AI contrast-clause structure
6. **Restraint as physical action, not declaration** — the extra ten seconds brushing teeth; the half-second pause on the top button — *show*, never *state*
7. **Cross-chapter object continuity** — the same object closes one chapter and opens the next

These are the seven hooks `forbidden-check` and `voice-check` are tuned to defend, and the seven hooks `review-captain` is tuned to verify the draft has not silently broken.

## How you know consistency held

This is the open evaluation question. The lab's working answer (to be tested formally in `research/`):

| Question | Operationalization |
|----------|-------------------|
| Did character voice hold? | Delete names; run voice-check on n random passages from the new chapter; count "can't tell who" returns |
| Did plot causality hold? | Trace each major event in the new chapter back to a setup in earlier chapters; count uncaused beats |
| Did the aesthetic hold? | Compute textural distance from baseline chapter; flag passages with > σ shift |
| Did the do-not-debate list hold? | Audit the captain's ruling: did it propose anything on the forbidden list? |

These four metrics are the seed of the consistency evaluation that will land in `research/02-evaluation-metrics.md` in v0.2.

## What this lab is not claiming

This is not "we solved consistency." It is **"we shifted consistency from a retrieval problem to a workflow problem, and the workflow gives us specific things to test."**

The shift matters: it makes the failure modes diagnosable. When drift happens (it will), you can ask which mechanism broke — SOUL contract? do-not-debate list? voice-check coverage? — and fix the specific mechanism, instead of vaguely "trying again with more context."

---

→ Back to [agent memory](./agent-memory.md)
→ Next: `outline-evolution.md` (v0.2)
