---
name: network-health-dashboard
description: Use when a network admin or org-level user asks for a cross-plant view of how their church-planting network is doing — "how are all our plants doing", "network overview", "show me the network status", "network dashboard", "how's the network", "give me the state of the network". Requires the LaunchPath MCP tools network_overview and list_plants. Do not use for a single-plant question (route that to plant-deep-dive or launch-roadmap instead), a pure blockers/stalled-plants question (stalled-plant-alert), or a vitals-and-check-ins question (network-scorecard-review).
---

# Network Health Dashboard

## Tools

- `network_overview` — the primary source. Returns every plant the caller oversees (coach assignments + org plants), worst-first, with progress, behind-pace count, days-to-launch, and STALLED flags (no completions in 3+ weeks), plus this month's scorecard check-in status for plants that run one, and a rollup of which roadmap areas plants struggle in most across the network.
- `list_plants` — use only if `network_overview` returns fewer plants than expected, to confirm the full set the account can see.

## Workflow

1. Call `network_overview`. It's already sorted worst-first — don't re-sort into a happier order.
2. Build the dashboard from what it returns. Do not call `get_plant_overview` or `find_bottlenecks` per plant unless the user asks to drill into a specific one — that's `plant-deep-dive`'s job, not this skill's.
3. Include the check-in summary the tool returns as its own small section — how many scorecard-running plants have submitted this month, and which are still open. Only plants with vitals appear there; a plant with none isn't behind, it just doesn't run a scorecard.
4. If the user follows up about the numbers inside those check-ins, that's `network-scorecard-review` — hand off rather than calling `network_scorecard` from here.
5. If `network_overview` says the account oversees no network plants, tell the user plainly and suggest `get_plant_overview` for their own plant instead of fabricating a network view.

## Artifact

Render a grid of plant cards as a visual (an artifact in chat, or an inline widget where available): one card per plant showing name, current roadmap stage/progress %, days to launch, and a health indicator — green (on pace), yellow (behind pace), red (STALLED). Sort worst-first, matching the tool's own ordering. Do not average across plants into a single network-wide percentage as the headline — a network health view should let the worst plants stay visible, not get smoothed into a mean.

## What not to do

- Don't invent a network-wide "progress_report" or "find_bottlenecks" call — those tools are plant-scoped only; per-plant drill-down belongs to other skills.
- Don't reorder plants to lead with good news — worst-first is the point of this view.
