---
name: weekly-check-in
description: Use when a planter wants to walk through and update their tasks conversationally — "let's do my weekly check-in", "help me update my tasks", "mark these done", "I finished X", "push this task's due date back", "let's go through what I did this week", "add a note to this task". Requires update_task_status, set_due_date, set_task_notes, add_task_comment, assign_task, week_ahead, and my_tasks. Writer-only (planter/team_member role) — see permission note below. Do not use for read-only weekly planning (this-weeks-focus).
---

# Weekly Check-in

The one skill in this set that writes. Everything else in this plugin only reads LaunchPath data — this one changes it, so move carefully.

## Permission note

LaunchPath's write tools (`update_task_status`, `set_due_date`, `set_task_notes`, `assign_task`) only work for the `planter` or `team_member` role on a plant; coaches are read-only by design. If a write call returns "Read-only access," don't retry or work around it — tell the user plainly that their role doesn't allow edits on this plant and stop there.

## Tools

- `week_ahead` / `my_tasks` — pull the working set to walk through.
- `update_task_status(task, action)` — `start`, `complete`, `skip`, or `reopen`. Completing or skipping reports an "unlock cascade" (what newly opened up) — always relay that, it's often the most useful part of the response.
- `set_due_date(task, due_date)` — `YYYY-MM-DD` or `none` to clear.
- `set_task_notes(task, notes)` — **replaces** the notes, it does not append. Call `get_task` first if the intent is to add to existing notes, then submit the combined text.
- `add_task_comment(task, body)` — both role-gated (planter/team_member, same as the other write tools) and license-gated (team collaboration is a licensed feature). If it fails, check which: a "read-only" style message means the role restriction, a licensing message means the plant needs an active license for team comments — relay the actual reason rather than assuming it's always the license.
- `assign_task(task, assignee)` — resolve the person via `get_team` first if the name is ambiguous; `"none"` unassigns. Note that coaches can't be assigned tasks — if the user tries, say so rather than letting the tool error read as a mystery failure.

## Workflow

Pull `week_ahead` or `my_tasks`, walk through items one at a time or as a batch the user specifies ("mark these three done"). For each status change, relay the unlock cascade from the tool's response — "completing X also opened up Y and Z" is exactly the kind of momentum a planter wants to hear. Confirm before completing or skipping more than a small handful of tasks at once (a batch "mark my whole week done" is worth a quick "confirm these five?" before firing off five calls) — but don't require confirmation for a single, explicitly requested change.

## What not to do

- Don't call `set_task_notes` without reading current notes first if the user's intent is "add a note" rather than "replace the notes" — it overwrites.
- Don't attempt a write action after a "Read-only access" error — surface it and stop.
- Don't batch-complete a long list of tasks without a quick confirmation first.
