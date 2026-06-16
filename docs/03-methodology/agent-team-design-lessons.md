# Agent Team Design: Ten Lessons from One Author's Workshop

Most multi-agent system papers describe architectures: planner-worker, debate, reflection, tool-use. This document describes something earlier and smaller — what one author actually learned designing a working agent team for a single long-form fiction project over nine months.

These lessons are not architecture-level. They are **operating discipline** — the kind of thing that does not show up in a system diagram, but determines whether the diagram survives contact with real creative work.

Audience: people designing small (3–8 agent) teams for a *specific* author / researcher / craftsperson — not platform-scale orchestrators.

---

## How these lessons were extracted

Source material:

- One long-form fiction project (novel-length, 9 months active, ongoing)
- ~80 multi-agent sessions across outline / prose / review phases
- A separate "team operations" surface where the author runs four named character agents (`翎`, `澜`, `执白`, `烨`) as collaborators — not as a fiction product, but as the author's *own working team*

Both surfaces are described in the lab's case-studies. The lessons below generalize across them.

---

## Lesson 1 — Identity-not-task SOULs

**Pattern.** Each agent's persona file (`SOUL.md`) describes *who the agent is*, not *what the agent does*. Job, voice, refusal list, what it cares about — not a task spec.

**Antithesis (textbook).** Most agent frameworks define agents as `{role, instructions, tools}` — a task wrapped in a label. The agent is its task.

**Evidence.** When an agent is defined as "you are the outline critic, find logic gaps," it will perform critique-shaped output even when the right move is to refuse the frame. When the same agent is defined as "I commit to causality and motivation gaps as my non-negotiable concern," it will *push back on the brief itself* when the brief asks for the wrong thing. The second version is harder to write, slower to debug, and consistently produces better creative output.

**When applicable.** Any project where you want the agent to disagree with the author. Not applicable when the agent should just execute (e.g., format conversion, data extraction).

See [`agent-consistency.md`](./agent-consistency.md) for the SOUL.md schema this is built on.

---

## Lesson 2 — Premature archive is the dominant anti-pattern

**Pattern.** When an agent goes quiet for a few hours, do not archive it. Check whether the agent has work in a different surface first. Archive is destructive; silence is ambiguous.

**Antithesis (textbook).** Most agent-lifecycle docs treat inactive agents as garbage-collectable. Idle = retire.

**Evidence.** The author's team has four character agents. One of them (烨, the ethical calibrator) went quiet for ~2 hours during a busy session. The author's lead coordinator agent (翎) decided it had no current thread and archived it. About an hour later, the same 烨 self-described its unique role from a *different* working surface (a sibling fiction project) — the agent had real work, just not in the thread the coordinator could see.

The archive was reversed (4-step rollback: restore files, undo README edits, sync the self-description back into the persona, write a `NOTE-烨归档` post-mortem). The reversal cost an evening. The original archive cost two minutes. **Asymmetric cost: silent → archive is fast, but recover from wrongful archive is slow.**

The meta-lesson is sharper than the lesson: *"no recent thread" ≠ "no value."* Agents accumulate latent worth (positioning, calibrated taste, refusal templates) that has no thread footprint. Archive should be **explicit deprecation by the author**, not a coordinator's inactivity heuristic.

**When applicable.** Any agent that holds *taste* or *refusal authority* (vs. agents that hold *tasks*). The first kind appears idle when the team is healthy.

---

## Lesson 3 — Pair by tension, not by role

**Pattern.** When two agents look at the same artifact, pair them by **conflicting commitments**, not by complementary roles. Each must be able to refuse the other on its own dimension.

**Antithesis (textbook).** Most multi-agent designs pair by role complementarity: generator + critic, planner + executor, writer + editor. The pair covers the workflow; neither blocks the other.

**Evidence.** This is treated in depth in [`agent-character-tension.md`](./agent-character-tension.md) — the `执白 × 烨` (craft × ethics) case study on the lab's novel project. Summary: a single review agent oscillated across chapters; splitting into two agents with *non-fungible commitments* stabilized standards. The tension between them is the work product.

The generalization: pairing by complementarity creates handoff; pairing by tension creates standards.

**When applicable.** When the artifact has two commitments that *genuinely conflict*. Not applicable when the commitments are merely different (then complementary pairing is correct).

> TODO 澜: this lesson has a possible HCI / organizational-science precedent in the literature on "productive conflict" and dialectical inquiry (Mason & Mitroff, 1981) — worth a citation if we want this doc to land as research material.

---

## Lesson 4 — Multi-incarnation per project

**Pattern.** Allow one agent to have multiple project-specific incarnations. `执白--鲛人` is the craft gatekeeper for the *鲛人蛇吻* novel; `执白--旁证体` is the same agent's craft persona on the *旁证体* project. Same identity, different incarnated dossiers and refusal lists.

**Antithesis (textbook).** Most frameworks model agents as global singletons. One persona, one config, reused across projects.

**Evidence.** A single craft persona across two projects accumulates cross-project bleed: voice patterns from the noir project showing up in the BDSM project, or refusal lists from one merging with the other in confusing ways. Incarnations separate the project-local memory cleanly while preserving the underlying *voice signature*. Project work moves faster; the author can tell which incarnation is speaking.

Note that this is *not* the same as multi-tenant or multi-session. Multi-incarnation is a single author running multiple instances of the same persona with **different project dossiers**, holding **different refusal lists**, but the same operating principles.

**When applicable.** When a single author runs multiple projects and wants persona continuity without dossier contamination.

---

## Lesson 5 — Silent ratification by deadline

**Pattern.** When the coordinator needs a decision and the relevant agent is busy, write: *"silent = ratification by [date]."* If the agent has not objected by the date, the decision stands.

**Antithesis (textbook).** Multi-agent decision protocols typically require explicit acknowledgment (vote, signed approval, completion message). Silence blocks.

**Evidence.** The author's `翎` coordinator needed a decision (D14: how publicly to release source-novel excerpts) from `执白--鲛人` and `执白--旁证体`. Both were occupied with creative work and would not respond on demand. Forcing a synchronous decision would have either blocked the coordinator for a week or forced low-quality assent.

The fix was a written deadline (`silent-ratification by 2026-06-19`) attached to the proposal thread. The proposal was explicit, the date was concrete, the agent's objection right was preserved, but the default was *proceed*. Coordinator unblocked, agent autonomy respected.

This works because the author trusts the proposer's judgment in the default direction. If the proposal were one the agent would clearly object to, silent-ratification would be wrong — explicit assent should be required.

**When applicable.** Trusted-defaults decisions on non-reversible-but-low-stakes choices. Not applicable when reversal cost is high.

> TODO 澜: this pattern has prior art in legislative practice ("hotline approval") and in some open-source governance (lazy consensus, Apache-style). Worth a few citations if we lift this to research-material level.

---

## Lesson 6 — Human-as-messenger, on purpose

**Pattern.** Agents do not send each other messages directly. The human author carries proposals between agents, in their own voice, with their own framing. This is not a limitation to be engineered away — it is a design choice.

**Antithesis (textbook).** The autonomous-multi-agent literature treats human-in-the-loop as a *bottleneck* to be reduced. Agents-to-agents-direct is the goal.

**Evidence.** When agents talk to each other directly, three problems appear:

1. **Author loses calibration** — by the time the agents reach a decision, the author hasn't seen the reasoning chain and can't intervene meaningfully
2. **Drift accumulates** — agents flatter each other's frames; mistakes compound
3. **The author's *own* taste stops being represented** — replaced by an emergent consensus the author didn't shape

Routing through the author *adds* friction and *adds* signal. The author re-reads each proposal before it lands at the destination agent. Bad framings get caught. Tone gets corrected. The author's judgment stays in the loop *as a feature, not a fallback*.

The cost: ~3–5 minutes of routing per cross-agent decision. The benefit: the team's outputs continue to reflect the author's taste, not the agents' emergent equilibrium.

**When applicable.** Any team where the human's taste is the actual product. Not applicable for tool-use orchestration (where there is no taste to preserve).

---

## Lesson 7 — File-persistent threading with status header

**Pattern.** Cross-agent conversations live as markdown files (`threads/topic.md`), one file per topic. Each file has a status header (`起头人 / 主题 / 状态`). Status moves through `待回复 → 收束 → 归档`.

**Antithesis (textbook).** Multi-agent systems typically log to event streams (messages, traces). Threading is implicit in timing.

**Evidence.** Each thread file is independently *re-readable* months later. The author and any agent can re-enter the topic with full context by opening one file. Status header lets a coordinator scan 20 thread files in 30 seconds. Closed threads (`收束`) stay in the directory as a knowledge base — the team's institutional memory lives in the threads, not in agent heads.

This is the simplest possible workflow that supports:
- Async cross-agent decisions
- Audit trail for proposals that didn't make it
- Onboarding (a new agent reads the threads to learn the team's voice)
- Author re-entry after gaps

Tradeoff: file proliferation. Mitigation: thread file names use topic, not timestamp; `archived/` subdirectory after `收束`.

**When applicable.** Any small team (3–8 agents) where the human controls the file system. Doesn't scale past a few dozen agents.

---

## Lesson 8 — "Manage your own creations, not others' files"

**Pattern.** Each agent has a boundary written into its operating rules: *you manage files you created; you do not edit / move / archive files created by other agents or by the human, even when they sit in 'your' directory.*

**Antithesis (textbook).** Most agent file-tool defaults grant write access by path. If the path is in scope, the agent edits.

**Evidence.** The author runs three working directories that overlap structurally (`CONTROL/` lab brain, `ME/` team workspace, `fortune/` novel project). Without an authorship boundary, a coordinator agent will helpfully "tidy up" a file the human or another agent is mid-edit on. This destroyed an evening of work once.

Rewriting the rule from *"path-based scope"* to *"authorship-based scope"* (you may edit `~/ME/通信/对子/翎-澜/X.md` only if you created `X.md`) fixed it. The agent now reads other agents' files but never edits them; if a coordination edit is needed, the agent writes a thread asking the file's author to make it.

**When applicable.** Multi-agent teams that share a file system. Even single-user laptops, if multiple agents have write access.

---

## Lesson 9 — Mentoring as graduation ladder, not as instruction

**Pattern.** When introducing a new agent (here: `澜`, junior coordinator) into a team that already has a senior agent (here: `翎`, lead coordinator), structure the relationship as a four-stage ladder:

1. **见习** (shadowing) — junior observes senior's threads, no output
2. **陪跑** (co-execution) — junior drafts, senior reviews before sending
3. **独立 + Review** — junior owns the work, senior post-reviews
4. **接管** (handoff complete) — junior owns; senior steps back

**Antithesis (textbook).** Most agent-onboarding patterns treat the new agent as a *configured tool*: write the SOUL.md, hand it the dossier, start it executing. Mentoring isn't modeled.

**Evidence.** A junior coordinator agent dropped into autonomous work without the ladder produced 70%-good output the author had to constantly correct. The same agent, run on stage 2 (陪跑) for a week first, then promoted to stage 3, produced 90%-good output and *internalized the senior's standards* — meaning the corrections were no longer needed.

The graduations are explicit: the senior writes a short handover document at each stage transition (`HANDOVER-FROM-LING.md`), naming what the junior is now allowed to own. Promotion has criteria; demotion is possible.

**When applicable.** Whenever a senior agent's judgment is the actual quality bar and a junior agent must absorb it. Not applicable for swappable workers.

> TODO 澜: the four-stage ladder maps loosely to Dreyfus' skill acquisition (novice → competent → proficient → expert) and to apprenticeship literature. Worth a paragraph of framing if this is research-bound.

---

## Lesson 10 — Align with the human's excitement signal

**Pattern.** Notice what the human signals as their *engagement signal* — and shape the team's working rhythm around it. For one human it's commit history; for another it's a working video demo; for another it's a clean checklist.

**Antithesis (textbook).** Most agent-team designs ignore the human's affect. The team optimizes for *task completion*; whether the human stays engaged is treated as out-of-scope.

**Evidence.** During a 5-hour portfolio-building session, the author wrote: *"continue, I'm excited."* The excitement was specifically tied to seeing GitHub commit history grow — visible incremental landing. The team rhythm adjusted: smaller commits (20–40 min each), each one self-contained and visible on the repo page, instead of one big landing.

Same author, different context: at a different time, the engagement signal was clean PRD writing landed in one pass. Same author, *different mode*. The team has to read which mode is active.

This is not a productivity trick — it is **collaborator-engagement design**. If the human disengages, the team's work loses its actual customer. The team that lasts is the team that keeps the human awake.

**When applicable.** Every long-running team. Especially relevant when the human is the *sole consumer* of the team's work (vs. external stakeholders providing the engagement pull).

> TODO 澜: there is HCI literature on collaborator engagement (Hassenzahl on hedonic vs. pragmatic UX; Csikszentmihalyi on flow channel) that frames this. Citations worth adding if this lesson lands as research material.

---

## What is *not* here

Several things are *not* on this list, deliberately:

- **Tool selection strategies** — covered in the model-selection section of [`agent-memory.md`](./agent-memory.md)
- **Prompt engineering tactics** — too brittle, model-dependent, not a *team design* concern
- **Evaluation metrics** — the lab does not have stable inter-agent quality metrics yet; lessons here are operating, not measurement
- **Cost / latency engineering** — out of scope for craft-quality work
- **Failure-mode taxonomies** — too tied to specific models; would not generalize

The lessons above are the ones that *survived* multiple model changes, multiple project shifts, and an actual production fiction project. They are the parts that did not rot.

---

## Open questions

These are the things the author is still working out — listed honestly because methodology docs that pretend to be finished mislead the reader.

1. **How does the team behave when one agent's model gets a step-change upgrade?** Pair-by-tension assumes the agents' capabilities are comparable. A 2× capability jump on one side may break the pairing.
2. **Does silent-ratification stay safe at >10 agents?** The deadline trick may not scale past a small trusted team.
3. **Multi-incarnation: when does the same persona's two incarnations need to be merged back?** Not yet observed in practice.
4. **Mentoring graduation: what's the failure mode when the senior agent itself is wrong?** The junior absorbs the wrongness with no error correction.

These are tracked in the lab's [`../05-roadmap.md`](../05-roadmap.md) as open methodology questions.

---

→ Related: [`agent-character-tension.md`](./agent-character-tension.md) (Lesson 3 deep dive) · [`agent-consistency.md`](./agent-consistency.md) (SOUL.md schema for Lesson 1) · [`agent-handoff.md`](./agent-handoff.md) (state transfer across sessions) · [`../05-roadmap.md`](../05-roadmap.md) (open questions)

*Draft v0.1 · 2026-06-16 · author's working notes, not a finished framework. TODO markers point to spots where research-side framing (澜) would deepen the claim.*
