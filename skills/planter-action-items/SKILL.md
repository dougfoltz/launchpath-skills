---
name: planter-action-items
description: Use when a coach wants to know what their planters should be working on soon — "what should my plants be doing this week", "upcoming action items for my planters", "what's due next week for my plants", "my week ahead across plants". Requires network_overview (or list_plants) plus week_ahead called per plant. Do not use for a single plant's detail — that's plant-deep-dive.
---

# Planter Action Items

## Tools

- `network_overview` — get the set of plants this coach oversees.
- `week_ahead(plant, days)` — called once per coached plant (default `days=14` unless the user asks for a different window). Returns overdue tasks, tasks due within the window, and tasks due soon but still locked behind prerequisites.

## Workflow

Group the output by plant, sorted by due date within each group. For each item show: task title, due date (or "overdue by N days"), current status, and — since coaches are read-only in LaunchPath and can't change status or assign tasks themselves — a suggested talking point for the coach's next conversation with that planter rather than an action the coach can take directly (e.g. "ask if X is blocked" rather than "reassign X").

If a plant has nothing due in the window, say so rather than omitting it — a quiet plant is information too (it may mean genuinely ahead of schedule, or it may be worth checking why nothing's moving).

## Artifact

Skip a Gantt-style chart — a 7–14 day window with no cross-plant dependencies doesn't need one. Use a grouped, date-bucketed list instead: one section per plant, tasks listed under their due date, most urgent first. This scales better and reads faster than a timeline chart for this time horizon.

## What not to do

- Don't suggest the coach directly reassign, reschedule, or mark tasks — coaches are read-only in LaunchPath (`assign_task`, `set_due_date`, `update_task_status` all require planter or team-member role). Frame outputs as things to discuss, not actions to execute.
- Don't build a Gantt/timeline artifact for this skill — see above.
