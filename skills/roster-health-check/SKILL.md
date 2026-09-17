---
name: roster-health-check
description: Use for any leadership-roster question, whether asked by a coach about a plant they oversee or by a planter about their own team — "check [plant]'s leadership team", "who do we have at [plant]", "is [plant] fully staffed", "roster gaps at [plant]", "is my team fully staffed", "who's on my team", "leadership team for [plant]". Requires get_team and get_plant_overview. One skill covers both audiences — the only difference is pronoun framing ("your team" vs. "[plant]'s team"), not the underlying data or tool calls.
---

# Roster Health Check

## Tools

- `get_team(plant)` — roster with names, emails, roles, and open-task counts. Optional `plant` param — omit it when a planter asks about "my team" and the account has exactly one plant.
- `get_plant_overview(plant)` — for stage context (some roles matter more at certain stages, e.g. a Facilities lead becomes urgent approaching the Infrastructure stage).

## Workflow

Call `get_team`, then flag: vacant core roles (no one filling Lead Pastor / Admin-equivalent positions if the roster schema exposes role gaps), anyone new to their role, and anyone carrying an unusually high open-task count relative to others on the same roster (a sign of an under-staffed area, not necessarily a problem with that person). Cross-reference `get_plant_overview`'s current stage to note if a role gap is becoming urgent (e.g. no one assigned to Facilities tasks as the plant nears that stage).

Match the pronoun to the caller: a planter asking about "my team" gets "your roster"; a coach asking about a plant they oversee gets "[plant]'s roster."

## Artifact

A roster table: role, person, tenure in role, status (active/interim/vacant). Optionally a simple ring/chord visual showing roles filled vs. vacant if the user wants something more visual than a table — keep this optional, most roster checks are quick enough to be text-only.

## What not to do

- Don't build a separate skill or duplicate logic for "my roster" vs. "the plant's roster" — this is intentionally one skill for both audiences.
- Don't speculate about *why* a role is vacant (funding, fit, etc.) — the tools expose roster and task data only, not the reasons behind staffing decisions.
