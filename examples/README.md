# Examples

This directory contains the **clone-and-run** material of this lab.

It splits into two kinds of content with very different reading modes:

| Subdirectory | What it is | How to read it |
|--------------|-----------|----------------|
| [`workflow-template/`](./workflow-template/) | **Clone, fill in placeholders, run.** | Copy a template directory, replace the placeholders with your domain-specific content, run via your orchestrator of choice. |
| [`case-studies/`](./case-studies/) | **Read to understand, not to clone.** | Real cases that show how the workflow produced specific work products. You're reading these to evaluate whether the methodology applies to your problem. |

If you came here as a **practitioner looking to try the workflow**, start with `workflow-template/`. If you came here as a **PM / researcher evaluating whether this methodology fits your domain**, start with `case-studies/`.

---

## workflow-template/

Skeletons that encode the structural design without exposing project-specific voice (per [`DECISIONS.md`](../DECISIONS.md) D06 — "结构公开 / 咒语藏").

| Template | Status | What it provides |
|----------|--------|------------------|
| [`4-agent-outline/`](./workflow-template/4-agent-outline/) | ✅ v0.1 | Four-agent outline discussion (diverger / critic / aesthete / captain) with R1 / R2 / arbitration / ruling flow. Includes SOUL placeholders and orchestration pseudocode. |
| [`5-agent-review/`](./workflow-template/5-agent-review/) | 🚧 v0.2 placeholder | Five-agent prose-review team (rhythm / blocking / voice / forbidden / captain). v0.1 ships the README only; full template lands v0.2. |

**To use a template**:

1. Read the SOUL templates and replace the placeholders with your domain-specific commitments (your project's job, boundaries, dimensions, output format)
2. Read the orchestration flow and adapt to your orchestrator (OpenClaw / LangGraph / AutoGen / CrewAI / whatever you have)
3. Build an input package per your project's locked facts + author brief
4. Run a single session and observe whether each agent stays in its lane

If any agent's refusal rate is 0 after a session, your template fill is incomplete (per [`agent-character-tension.md`](../docs/03-methodology/agent-character-tension.md)).

## case-studies/

Real cases from production deployments of this workflow. Each case study includes (or will include) **an excerpt + the creative intent + what the workflow showed about itself**.

| Genre bucket | Status | Cases |
|--------------|--------|-------|
| [`01-folklore-mystery/`](./case-studies/01-folklore-mystery/) | ✅ v0.1 skeleton | `case-旁证体.md` (craft baseline), `case-鲛人蛇吻.md` (workflow validation) |
| `02-mystery/` | 🚧 v0.4 (planned) | 本格 / 社会派, per [`DECISIONS.md`](../DECISIONS.md) D10 |
| `03-???` | 🚧 v0.4 (placeholder) | psychological-character-study endorsed by both 执白 incarnations; 康康 to ratify per D10 |

**Why two cases in folklore-mystery, not one**: Per [`DECISIONS.md`](../DECISIONS.md) D08, the two cases sit in **ordered progression** — 旁证体 is the craft baseline (hand-written) and 鲛人蛇吻 v2 is the workflow validation (multi-agent-augmented). Reading one without the other loses the central design choice. See [`case-鲛人蛇吻.md`](./case-studies/01-folklore-mystery/case-鲛人蛇吻.md) "Relation to 旁证体".

**Excerpt access**: Excerpts published here are released under CC BY 4.0 (see [`LICENSE`](../LICENSE)). Full source novels remain under the author's copyright; collaboration-request access for academic reproducibility — see [`LICENSE`](../LICENSE) Part 3 and [`DECISIONS.md`](../DECISIONS.md) D14 (pending).

## What this directory does NOT include (v0.1)

- Filled SOUL templates with production prompts. By design — per D06, the templates are placeholders.
- Full case-study excerpt text. Pending excerpt selection by 执白 + pre-screen coordination by 澜. Lands v0.2.
- Live runnable scripts. By design — the orchestrator is yours to bring; the lab is methodology, not runtime.

---

→ Back to [README](../README.md)
→ Related: [`docs/02-architecture.md`](../docs/02-architecture.md), [`docs/04-genre-adaptation.md`](../docs/04-genre-adaptation.md)
