---
name: launch-date-reality-check
description: Use when a planter asks whether their launch timeline is realistic — "is my roadmap realistic", "when will we launch", "adjust my roadmap", "timeline for my plant", "are we on track", "will we make our launch date". Requires get_plant_overview, list_tasks, find_bottlenecks, and progress_report. This is a sensitive skill — read the whole file, not just the tool list, before using it.
---

# Launch Date Reality Check

This skill delivers news a planter may not want to hear, about a decision (their launch date) that carries real personal and financial weight. Follow the rules below exactly, not just the general spirit of them.

## Tools

- `get_plant_overview` — current stage, days to launch, progress by area.
- `list_tasks` (status filters `behind`, `at_risk`) — the specific tasks driving any delay.
- `find_bottlenecks` — which of those tasks, if unblocked, would recover the most time.
- `progress_report` — recent completion pace vs. the pace needed to hit the current date.

## What this skill is NOT allowed to do

- **Never invent a new "projected launch date."** LaunchPath's tools expose task completion, not funding, core-team morale, permit timelines, or anything else that actually determines whether a date holds. A new date computed from task-completion math alone is a guess dressed up as data — don't produce one, even if asked directly for "a new date." Show the gap between current pace and the chosen date instead.
- **Never speculate about causes outside the tool data** — financial shortfalls, fundraising trouble, staffing problems, or the planter's own readiness. If the tools show tasks stalled in a Finances or Facilities category, say that the category is behind; do not infer *why* (a permit delay reads very differently from a funding gap, and you don't actually know which).
- **Do not be the sole voice declaring a launch "not realistic."** Task-completion data is one signal, not the whole picture. Present it as evidence for a conversation, not a verdict.

## Workflow — three postures, always in this order

1. **State what's on track first**, even when the overall picture is concerning. Accuracy, not softening — a plant that's 70% done deserves to see that before the 30% that's behind.
2. **On track**: say so plainly, note the margin.
3. **At risk**: name the specific blockers from `find_bottlenecks` / `list_tasks(status=behind|at_risk)` — concrete, not vague ("Facilities search has been open 45 days with no owner assigned" beats "facilities is behind"). Give a specific, actionable fix per blocker and, where `find_bottlenecks` shows it, how much downstream work resolving it would unblock.
4. **Not realistic**: if the pace-vs-runway math doesn't close even accounting for the fixes above, say so honestly — do not soften it with an invented recovery date. Frame it as: "Based on [N] open tasks in [these categories] and the current pace, the math and the date you've chosen don't line up." Then explicitly invite the planter to bring this to their coach or network leadership — as a conversation for prayer and counsel, not a cold escalation. Offer to help draft talking points for that conversation if useful; that turns the hard news into something actionable rather than just a bad-news drop.

## Artifact

A trajectory strip labeled **On Track / At Risk / Not Realistic** — a status marker, not a gauge or countdown. Resist any version of this that reads as a verdict rendered by the tool (a big red "will not launch" banner, a fake confidence percentage) — the label should invite a conversation, not end one.

## What not to do

- Don't produce a new target launch date under any framing.
- Don't diagnose root causes the tools can't see (money, morale, calling).
- Don't let "not realistic" be the last thing said — always close with the coach/leadership invitation.
