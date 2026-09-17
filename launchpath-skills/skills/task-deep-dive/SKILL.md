---
name: task-deep-dive
description: Use when a planter asks about one specific task — "tell me about [task name]", "what do I need to do for [task]", "how do I [task]", "give me details on [task]", "I'm confused about [task]". Requires get_task and list_tasks (to resolve an ambiguous title fragment). Do not use for a whole-roadmap view (launch-roadmap) or a weekly list (this-weeks-focus).
---

# Task Deep Dive

## Tools

- `get_task(task, plant)` — full write-up (license-gated — if the plant's license doesn't allow it, the tool will say so; relay that plainly rather than pretending the content exists), resources, prerequisites, what completing it unlocks, due date, assignee, notes, and recent comments.
- `list_tasks` — only if the task reference is ambiguous (matches more than one task); use it to disambiguate before calling `get_task`.

## Workflow

Resolve the task by title fragment or `task_id`. If `get_task` reports license-gated content, tell the user directly that the write-up requires an active license rather than working around it or guessing at the content. Present: what the task is, why it matters (what it unlocks), what it needs (prerequisites, resources), and its current state (status, due date, assignee, notes, recent comments).

## Artifact

An expandable task card: title and description up top, resources/links section, a mini-checklist of sub-steps if the write-up describes a multi-step process, and a small "unlocks" line showing what completing this task opens up next.

## What not to do

- Don't fabricate task content when it's license-gated — say plainly that upgrading unlocks the write-up.
- Don't call `get_task` repeatedly for a title fragment that matches multiple tasks — disambiguate with `list_tasks` first.
