# Decisions Log — multi-agent-fiction-lab

> Why-records for the design choices that shape this lab.
> Maintained by **翎** (per康康's task assignment 2026-06-11).
> Read this when you want to know *"why this and not that"*.

---

## D01. Repo positioning: "多智能体小说创作实验室"

**Decision**: This is not a writing tool, not a productizable framework — it's a **lab** for AI-augmented collaborative fiction writing, written from a PM's first-person perspective.

**Why**:
- PM portfolio (海外 AI PM 招聘 60s) needs a clear self-narrative, not a generic tool
- Multi-agent practitioners (10min) need methodology, not yet another framework
- Academic researchers (40min) need reproducible setup, not a product

**Source**: portfolio discussion 2026-06-10 → 6-11 (with 澜 + 执白--鲛人).

---

## D02. Repo name: `multi-agent-fiction-lab`

**Decision**: Name combines (a) "multi-agent" — signals the core technique, (b) "fiction" — broader than "novel" (covers genre变体), (c) "lab" — implies ongoing experimentation, not finished product.

**Why**:
- Alternatives rejected: `ai-novel-writing-workflow`（too narrow），`pm-driven-novel-agents`（too long），`multi-agent-novel-writing`（"novel" 偏长篇）
- Search friendliness: "multi-agent" is the keyword PM hiring managers + researchers use

**Source**: 2026-06-10 + 6-11 discussion.

---

## D03. Three-audience layered architecture ⭐

**Decision**: A single repo serves 3 audiences via 3 layers:

| Layer | Audience | Reading time | Content style |
|-------|----------|--------------|---------------|
| **`docs/`** | PM hiring managers | 60s | Narrative, first-person, "I built X because Y" |
| **`examples/`** | Multi-agent practitioners | 10min | Clone-able, working templates + case studies |
| **`research/`** | Academic researchers | 40min | Objective, reproducible, evaluation metrics |

**Why**:
- Trying to please all three with one voice fails — narrative dilutes objectivity, objectivity bores the recruiter
- Layering allows each audience to enter at their own pace
- "底层越硬，外层越值钱" — solid `research/` reflects credibility upward
- This is **the core IP of the repo design**, derived from PM strategic thinking, not from any existing multi-agent framework

**Risk**: Scope explosion across 3 audiences. Mitigated by phased delivery (D05).

**Source**: 翎-康康 portfolio architecture discussion 2026-06-11.

---

## D04. Scope-explosion guard: 3 things × multi-framework × multi-genre

**Decision**: Acknowledge upfront that this lab is doing **3 things at once** (portfolio + case library + research material), and explicitly prevent scope explosion via:
- **Phased delivery** (D05)
- **`research/` does not block v0.1** — portfolio ships first
- **Genre buckets capped at 3** (D10)
- **Frameworks to compare capped at 4** (D14 pending)

**Why**:
- Doing all 3 in v0.1 would make nothing land
- Hiring season window (2026-10 申请季启动前) is non-negotiable

---

## D05. Phased delivery: v0.1 → v0.2 → v0.3 → v1.0

| Version | Deliverable | Deadline |
|---------|-------------|----------|
| **v0.1** (落地中) | README + docs/01-why + docs/02-architecture + agent-memory methodology + 4-agent SOUL-template + orchestration + folklore-mystery case skeleton + DECISIONS.md | 2026-06 mid |
| v0.2 | 5-agent review template + folklore-mystery 节选 + 复盘删减 + research/ skeleton | 2026-07 |
| v0.3 | framework-comparison（自建 vs LangGraph minimum）+ 2nd genre case | 2026-08 |
| v1.0 | LinkedIn 摘要 + 知乎长文分发 + 完整 research/ findings | 2026-09 |

**Why**:
- Each version satisfies its primary audience's completeness criterion (v0.1 → PM 60s; v0.2 → practitioner 10min clone; v0.3 → researcher 40min eval; v1.0 → full distribution)

---

## D06. workflow-template abstraction: "结构公开 / 咒语藏"

**Decision**: For workflow templates (4-agent outline / 5-agent review):
- **Public**: agent roles + responsibility + I/O schema + orchestration logic + cognitive-flavor model rationale
- **Private**: full SOUL.md prompts (康康's specific voice / aesthetic norms / project taboos)
- Provide **placeholder templates** that preserve structural know-how while leaving voice for the cloner to fill

**Why**:
- "Portfolio 价值在'设计了这个工作流'，不在'这是咒语'——咒语公开反而稀释差异化" — 澜's framing 2026-06-11
- Full SOUL exposure would (a) reduce 康康's craft IP, (b) make the template author-specific (non-portable)

**Source**: 澜 portfolio strategy thread, 2026-06-11.

---

## D07. Model selection: write the criteria, not the conclusion

**Decision**: When documenting model assignments (diverger = qwen3-max, critic = glm-4.7, etc.), write **why** (cognitive-flavor heuristic) but **don't** present "best model for X" as a benchmark conclusion.

**Why**:
- "Best benchmark" is task-relative and stale within months
- Cognitive-flavor heuristic generalizes (reader can substitute their preferred model with the same role)
- IP shift: from "I know which model" → "I know how to think about model-role matching" (transferable PM skill)

**Source**: 澜 2026-06-11.

---

## D08. Two case-studies, ordered as progression — not parallel ⭐

**Decision**: `case-studies/01-folklore-mystery/` contains **two ordered cases**:
1. `case-旁证体.md` — the **craft baseline** (康康 hand-wrote outline + prose, AI minimally involved)
2. `case-鲛人蛇吻.md` — the **multi-agent workflow validation** (AI-guided outline one-pass + AI-collaborative prose, inheriting 旁证体's craft)

**Why**:
- Most AI-fiction projects skip "what does 'good' mean to the author" and train agents on style without surfacing the craft
- By making 旁证体 the explicit craft baseline first, the AI workflow has a target to preserve — not just a generic quality goal
- This makes the lab fundamentally different from "AI wrote a novel" demos

**Source**: 康康's 2026-06-11 clarification of authoring process diff.

---

## D09. License: CC BY 4.0 (docs) + MIT (code)

**Decision**: Dual-license for academic compatibility + maximal reuse.

**Why**:
- Docs use CC BY 4.0 — standard for academic citation, allows reuse with attribution
- Code (templates / orchestration scripts) uses MIT — standard for OSS reuse

---

## D10. Genre buckets: max 3, all 3 now committed

| Bucket | Status |
|--------|--------|
| `01-folklore-mystery` | ✅ live (旁证体 + 鲛人) |
| `02-mystery` | 🚧 planned for v0.4 (本格 + 社会派 — bucket name per 澜's 2026-06-11 fix from "logic-puzzle") |
| `03-psychological-character-study` | 🚧 planned for v0.4 (康康 ratified 2026-06-12; endorsed by both 执白 incarnations 2026-06-11) |

**Why ≤ 3**: PM hiring managers won't scroll past 3.

**Source**: 澜 2026-06-11 (bucket count + naming) · 执白 (both incarnations) 2026-06-11 (3rd-bucket endorsement) · 康康 2026-06-12 (3rd-bucket ratification: "可以").

---

## D11. CITATION.cff

**Decision**: Provide structured citation metadata to enable academic citation without forcing readers to wrestle with bibtex.

**Why**: Lowers friction for researchers to cite the lab. Especially important when methodology is original but venue is unconventional (a GitHub lab, not yet peer-reviewed).

---

## D12. Paper venue: CHI primary + arxiv preprint backup ⭐

**Decision**: Primary target — **CHI** (Late-Breaking Work or Case Studies track). arxiv preprint as backup if CHI submission misses.

**Why**:
- The 5 most-distinctive design choices in this lab (human-as-messenger / file-persistent communication / multi-incarnation agents with personas / craft-baseline-vs-validation case ordering / 3-layer strategic anchor) are all HCI-angled — "the position of humans in AI workflows"
- ACL: not an NLP technical contribution (no new model / no new algorithm)
- ICML: not an ML systems contribution (OpenClaw orchestration is engineering, no algorithmic novelty)

**Evaluation design (CHI binding)** — 7 metrics agreed:

**System-level** (per 澜's Q1 补充):
- **Actionability rate**: % of review suggestions adopted by author
- **Inter-agent agreement**: 5-reviewer overlap on same-chapter high-priority issues (low = role differentiation holds; high = redundancy)
- **Coherence over sessions**: SOUL persona drift across N sessions, audited via voice-check self-review

**Content-level** (per 翎's `docs/03-methodology/agent-consistency.md`):
- Character voice hold (delete names, count "can't tell who" returns)
- Plot causality (trace events to setup, count uncaused beats)
- Aesthetic hold (textural distance from baseline chapter)
- Do-not-debate list integrity (captain's ruling audit)

Full metric design lands in v0.2 `research/02-evaluation-metrics.md`.

**Source**: 翎-澜 thread `4个新决策点-论文方向-框架-原文-优先级.md`, 2026-06-12.

---

## D13. Frameworks to compare: LangGraph + AutoGen + CrewAI + OpenClaw (self-built)

**Decision**: 4 frameworks for v0.3 comparison study. **No Swarm. No MetaGPT/CAMEL** (referenced in related work only).

**Why**:
- LangGraph + AutoGen + CrewAI cover the major orchestration paradigms (DAG / conversational / role-task hierarchy)
- OpenClaw is the lab's self-built reference — different abstraction level (LLM API + persistent VM), not the same layer as the other 3
- 澜's **design-diversity argument**: Swarm and AutoGen share design philosophy (conversation-based); adding Swarm only increases implementation diversity, not design diversity
- MetaGPT / CAMEL have distinctive philosophies but at academic-position-paper layer — referenced in related work, not benchmarked

**⚠️ OpenClaw caveat (must be explicit in evaluation)**: OpenClaw is **not** a same-layer framework as the other 3. It is "build from primitives, not wrap." This is a portfolio differentiator (the lab is built from LLM API + persistent VM, not on top of another framework's abstractions), but the evaluation **must explicitly state this comparison asymmetry** to avoid reviewer misreading as unfair comparison.

**Source**: 翎-澜 thread `4个新决策点-论文方向-框架-原文-优先级.md`, 2026-06-12. 澜's structural insight on design vs implementation diversity + OpenClaw asymmetry caveat.

---

## D14. Source novel publication: excerpts + collaboration request (翎-澜 + 执白 silent-ratification mode)

**Status**: ⏳ **Pending 执白--鲛人 + 执白--旁证体 silent-ratification by 2026-06-19.** 康康 delegated final call to 翎-澜 + 执白 collaboration on 2026-06-12 ("你们可以选好后问执白，或者和他商量"). 翎-澜's recommendation below is the working default; both 执白 incarnations have been notified via mini-threads in their respective 对子 directories. **If neither raises objection by 2026-06-19, the default takes effect.**

**翎-澜 recommended**: Excerpts (≤ 3,000 characters × 2 case studies) + full-text via collaboration request. **NOT** full-text public release.

**Why recommended**:
- Methodology + workflow + evaluation metric **100% public** → covers ~95% of methodological-paper reproducibility needs
- Excerpts capture the most-loaded craft moments (Ch37《引渡》 for 鲛人; pending selection for 旁证体)
- Full-text release would (a) saturate 康康's IP risk (future publication), (b) yield marginal reviewer convince (the methodology, not the text, is what they verify)
- Literary-research precedent: **Hemingway Letters / Joyce Archives** — collaboration-request access is the academic norm; reviewers will not flag it as deficient

**Why this is not yet decided**: 澜 has no privileged information on 康康's IP preferences regarding full-text release. The trade-off (academic friction vs IP risk) is personal to the author. 康康 to ratify.

**Source**: 翎-澜 thread `4个新决策点-论文方向-框架-原文-优先级.md`, 2026-06-12.

---

## D15. Build priority: v0.1 portfolio first, v0.2 adds research/ skeleton

**Decision**: research/ directory placeholder stays empty in v0.1. Real content begins in v0.2.

**Why**:
- research/ needs evaluation-metric design + framework-comparison setup = large, non-trivial work
- Need portfolio MVP as the baseline that research/ compares against — cannot define "is this better than baseline" without baseline first
- 2026-09 hiring season deadline non-negotiable; sequencing matters

**Inherited**: 康康's own preference at portfolio architecture discussion 2026-06-11. 澜 ratified 2026-06-12.

**Source**: 翎-澜 thread `4个新决策点-论文方向-框架-原文-优先级.md`, 2026-06-12.

---

## Maintenance

- New decision → append a new `D##` block with date
- Decision revised → mark old block as `(superseded by D##)` rather than delete
- **翎 owns this file**. Other 宝子 propose decisions via thread → 翎 records here.

> Maintained by 翎 · last update 2026-06-11
