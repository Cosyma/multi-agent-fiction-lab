# 5-Agent Prose Review Team

> Status: **v0.2 (planned)**. This directory is a placeholder for the prose-review template, planned for v0.2 alongside the first case study completion.

## What this will contain (v0.2)

- `SOUL-template.md` — placeholder SOUL templates for the 5 prose-review agents:

| Role | Cognitive flavor | Suggested model |
|------|------------------|-----------------|
| **rhythm-check** (节拍) | broad surface to spot engine breaks | qwen3-max |
| **blocking-check** (调度) | sharp staging / positioning auditor | glm-4.7 |
| **voice-check** (声线) | taste-forward voice distinctiveness judge | kimi-k2.5 |
| **forbidden-check** (禁区) | fast pattern matching for author-intrusion / over-explain | gemini-2.5-flash |
| **review-captain** (收束裁决) | synthesis without flattening | claude-sonnet-4-6 |

- `orchestration.md` — sequential flow with gating logic:

```
1. rhythm-check FIRST (gate)
     ├─ if engine broken → STOP, fix structure before continuing
     └─ if engine ok → proceed

2. blocking-check + voice-check IN PARALLEL
     (independent dimensions, no cross-pollination)

3. forbidden-check AFTER (cleanup pass on prose tics)

4. review-captain CONSOLIDATES
     - merges overlapping findings
     - orders fixes by priority
     - rules on conflicts
```

## Why a separate team from outline

See `../../../docs/02-architecture.md#why-two-teams-not-one` for the rationale of splitting outline-level and prose-level concerns into separate teams with different cognitive flavors at different temperatures.

In short: outline debates structure; prose review audits a draft. Mixing them dilutes both.

## Reference (private)

Production implementation lives at `fortune/PROTOCOL_review_team.md` (康康's private OpenClaw setup). The v0.2 template will be the placeholder-version abstraction of that production setup, following the same "结构公开 / 咒语藏" principle as the 4-agent outline template (see `~/Documents/2026/multi-agent-fiction-lab/DECISIONS.md` D06).

## See also

- `../4-agent-outline/` — outline discussion template (v0.1, available now)
- `../../case-studies/01-folklore-mystery/case-鲛人蛇吻.md` — the case that will use this prose-review template
