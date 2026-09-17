---
name: coach-assignment-sync
description: Use when a network admin asks about coaching coverage — "who's coaching which plants", "show me our coaching load", "which coaches have capacity", "which plants lack a coach", "coaching assignments". Requires list_plants and get_team (called per plant). Do not use to assign a task to a person on one plant's team — that's a direct MCP tool call (assign_task), not this skill.
---

# Coach Assignment Sync

## Tools

There is no single tool that returns "coach → plants" across the network. Build it:

1. `list_plants` — every plant in scope.
2. `get_team(plant)` — called per plant. This already returns each person's role (including `coach`) and their open-task count, so no extra `list_tasks` calls are needed for load numbers.

## Workflow

For each plant, pull the roster, extract anyone with role `coach`, and aggregate across plants: which coaches appear on multiple plants, and what their combined open-task visibility looks like (note: coaches don't carry task load themselves since they can't be assigned tasks — "load" here means how many plants and how many total open tasks across those plants they're tracking, not tasks assigned to them personally).

Flag two things explicitly: plants with zero coach on the roster, and coaches attached to a number of plants that looks high relative to the rest of the network (a relative comparison, not a fixed threshold — you don't know their capacity, so phrase it as "coach X is on N plants, more than anyone else here" rather than asserting overload).

## Artifact

A simple table: coach name, plants coached, and combined open-task count across those plants. Sort by plant count descending so overloaded coaches surface first; put uncoached plants in their own callout below the table, not buried in it.

## What not to do

- Don't assert a coach is "overloaded" against an invented numeric threshold — you don't know anyone's actual capacity. Report the numbers and let the admin judge.
- Don't confuse a coach's open-task count with tasks assigned to them — coaches can't be assigned tasks in LaunchPath; the count reflects the plants they're overseeing, not their personal to-do list.
