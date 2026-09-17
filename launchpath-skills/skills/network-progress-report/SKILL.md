---
name: network-progress-report
description: Use when a network admin needs a formatted rollup for an external audience — "generate a report", "board update", "executive summary of our plants", "progress report for the network", "how many plants launched this quarter", "denominational update". Requires list_plants, progress_report (called per plant), and network_overview. Do not use for an internal quick-check ("how are we doing" — that's network-health-dashboard) or a blockers-only ask (stalled-plant-alert).
---

# Network Progress Report

## Tools

There is no network-wide `progress_report` — it's plant-scoped. Build the rollup by iterating:

1. `list_plants` — get the full set of plants in scope.
2. `progress_report(plant, since_days)` — call once per plant (default `since_days=30` unless the user names a different window, e.g. "this quarter" → 90).
3. `network_overview` — pull the STALLED/behind-pace context to add risk callouts the per-plant reports won't surface on their own.

## Workflow

Synthesize, don't just concatenate. Roll the per-plant `progress_report` calls into: total plants, count by stage, plants that completed a stage or launched in the window, aggregate completions vs. needed pace, and a top-5 risks section pulled from `network_overview`'s STALLED/behind-pace data. If the network has more than ~15 plants, ask the user whether they want the full per-plant breakdown or just the rollup — don't silently dump 15 plants' worth of detail into a "board update."

## Artifact

A stage-funnel chart: count of plants at each roadmap stage (Assessment → Core Team → Vision → Leadership → Infrastructure → Launch → Post-Launch). Pair it with a short highlights/risks text block — funnel charts are good for "where is everyone" but bad for "what changed" or "who needs help," which still need prose.

## What not to do

- Don't call `progress_report` without a plant when the user means "the whole network" — it will only cover whichever plant the tool defaults to, silently giving a partial answer.
- Don't present raw per-plant tool output as the "report" — this skill's value is the synthesis across plants.
