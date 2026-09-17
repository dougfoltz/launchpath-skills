---
name: coached-plants-summary
description: Use when a coach asks for a summary of the plants they personally oversee — "show me my plants", "what do I coach", "my coaching dashboard", "where are my plants in the pipeline", "check in on my plants". Requires network_overview (it's already scoped to plants the caller oversees), plus network_scorecard when the coach's plants report vitals. Do not use for a network admin's org-wide view (network-health-dashboard), for a vitals-and-check-ins question (network-scorecard-review), or for detail on a single plant (plant-deep-dive).
---

# My Coached Plants Summary

## Tools

- `network_overview` — this tool's description is literally "for coaches and network admins: every plant they oversee" — it's already scoped correctly for this skill with no extra filtering needed. It returns progress, behind-pace count, days-to-launch, STALLED flags, and each scorecard-running plant's monthly check-in status, worst-first.
- `network_scorecard` — optional second call, when `network_overview` shows the coach's plants are running scorecards and the coach wants the numbers behind the check-ins. It returns only the plants they coach.

## Workflow

Call `network_overview` and present it as the coach's personal dashboard, not a network-wide report — frame it as "your plants," not "the network." If it returns zero plants, say so plainly rather than guessing a cause (the account may not yet have coach role on any plant, or may only have a personal plant — suggest `launch-roadmap` for that case).

If the response carries check-in status, fold it in as one line per plant rather than a section — "August check-in in" or "still open." A plant with no vitals gets no check-in line at all, and that's correct: not every plant runs a scorecard. When the coach wants the actual numbers, follow with `network_scorecard`, and keep the vitals framed as God's work rather than the planter's scorecard — see `network-scorecard-review` for the fuller treatment.

## Artifact

A card per coached plant: name, location, lead planter (if available from context), current stage, % complete, overdue task count, and days to next milestone or launch. Order worst-first, matching the tool. Keep it lighter-weight than the network admin's dashboard — a coach typically has a handful of plants, not dozens, so cards can carry more per-plant detail than network-health-dashboard's grid.

## What not to do

- Don't call `list_plants` and try to guess which plants are "coached" from role data yourself — `network_overview` already does this correctly.
- Don't present this as a network-wide report to a coach who only oversees a few plants — keep the framing personal.
