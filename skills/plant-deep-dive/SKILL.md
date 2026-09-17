---
name: plant-deep-dive
description: Use when a coach (or network admin) wants a full picture of ONE specific plant — "deep dive into [plant name]", "detailed status for [plant]", "tell me everything about [plant]", "how are we really doing at [plant]", "prep me for my call with [plant]". Requires get_plant_overview, get_team, list_tasks, get_task, progress_report, get_scorecard, and find_bottlenecks, all scoped to that one plant. Do not use for a multi-plant rollup — that's coached-plants-summary or network-health-dashboard.
---

# Plant Deep Dive

## Tools, all scoped with `plant=<that plant>`

- `get_plant_overview` — days to launch, progress by area, tasks running behind, tasks that just opened up.
- `get_team` — roster with roles and open-task counts.
- `list_tasks` (status filters `behind`/`at_risk`) — the specific tasks driving concern.
- `get_task` — full detail on the 2–3 tasks that matter most, once identified.
- `progress_report` — recent pace vs. needed pace, feeds the "what's changed lately" section. Its scorecard block also carries the faithful actions the team finished, with outcome notes.
- `get_scorecard` — the plant's vision statement, key vitals against goal with their recent trail, this month's faithful actions, and whether the monthly check-in is in. This is the "how is the church actually doing" half of the picture, as opposed to "how is the project going."
- `find_bottlenecks` — which active tasks are holding back the most downstream work; this is the "what should the planter focus on" answer.

## Workflow

Resolve the plant name first if ambiguous (multiple plants matching a fragment) before calling anything else. Then build the snapshot in this order: stage + progress (`get_plant_overview`), the scorecard (`get_scorecard`) for vision and vitals, roster and any vacant/new roles (`get_team`), then the pointed stuff — behind/at-risk tasks and bottlenecks — with `get_task` detail only on whichever 2–3 tasks are most load-bearing. Close with a recommended action for the coach's next conversation with the planter, grounded in what `find_bottlenecks` surfaced.

Hold the two halves apart when you report them. Roadmap progress is the team's execution and fair to coach on directly. Key vitals are lag measures — God's work — so report them as prayer material, not as a performance review; a plant can be faithful and still have a quiet month. A missing check-in is worth mentioning as a gentle follow-up, never as non-compliance.

If this is being used to "prep for a call," lead with what's going well before the concerns — a coach walking into a conversation needs the full picture, not just the trouble spots.

## Artifact

A single-plant dashboard: stage indicator with time-in-stage, a roster panel showing roles filled vs. vacant, and a short list of the top blockers with who's assigned. Share the same card/grid visual language as `coached-plants-summary` and `network-health-dashboard` so a coach recognizes the drill-down as an extension of the summary view, not a different tool entirely.

## What not to do

- Don't call `get_task` on every task in the plant — only the ones central to the current concern or bottleneck.
- Don't skip straight to problems — state what's on track before what isn't.
