---
name: this-weeks-focus
description: Use when a planter asks what to work on soon — "what do I work on this week", "what's due from me", "my tasks this week", "upcoming for me", "tell me what's next". Requires week_ahead and my_tasks. Do not use for a full-progress question (launch-roadmap) or for actually updating a task's status (weekly-check-in).
---

# This Week's Focus

## Tools

- `week_ahead(days)` — default 14 days; overdue tasks, tasks due in the window, and tasks due soon but still locked behind prerequisites.
- `my_tasks` — tasks specifically assigned to this user if the plant has a team, behind-pace first.

## Workflow

Lead with overdue items, then due-soon items, sorted by date. For each: task title, due date (or days overdue), any blocker or dependency, and a one-line suggested action. If a task is "due soon but locked," say what it's waiting on rather than just listing it as upcoming — that's actionable information the raw due-date list would hide.

Keep the list to the 5–7 items that actually matter this week; don't dump the entire `week_ahead` window if it returns more than that unless the user asks for the full list.

## Artifact

A simple date-bucketed card list — task bubbles positioned on or grouped by due date, color-coded by roadmap area. Skip anything more elaborate; this is a short-horizon view and doesn't need a full timeline chart.

## What not to do

- Don't reach for `weekly-check-in`'s write tools here — this skill only reads and presents; if the planter wants to mark something done or reschedule mid-conversation, that's the trigger for `weekly-check-in`.
