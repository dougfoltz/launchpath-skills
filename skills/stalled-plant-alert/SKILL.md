---
name: stalled-plant-alert
description: Use when a network admin or coach asks specifically about blocked, stalled, or lagging plants — "which plants are stuck", "find our bottlenecks", "what's blocked across the network", "show me lagging plants", "network blockers", "who needs attention this week", "who do I need to call". Requires network_overview and, for drill-down, find_bottlenecks. Do not use for a general "how's everyone doing" question — that's network-health-dashboard.
---

# Stalled Plant Alert

## Tools

- `network_overview` — primary source. Its STALLED flag (no completions in 3+ weeks) and behind-pace counts are exactly this skill's subject matter.
- `find_bottlenecks` — plant-scoped only (it takes an optional `plant` param, not a network scope). Use it to drill into ONE flagged plant at a time, once the user picks one from the list or asks "why is [plant] stuck" — it walks that plant's dependency graph and ranks which active tasks are holding back the most downstream work.

## Workflow

1. Call `network_overview`, filter/emphasize plants that are STALLED or have a high behind-pace count.
2. Present a ranked list: plant name, days since last completion (or behind-pace count), and — if you already know it from `network_overview`'s area rollup — the struggling area.
3. Only call `find_bottlenecks(plant=...)` for a specific plant when the user asks to go deeper on it. Don't fan this out across every plant in the network unasked — that's expensive and usually more detail than the admin wants at a glance.
4. For each flagged plant, suggest a concrete next action (reassign the blocking task, escalate to the coach, or a specific unblock) rather than just reporting the stall.

## Artifact

Default to a ranked list with a severity chip per plant (e.g. "STALLED — 34 days", "Behind — 3 tasks"). Only reach for a heat-map (plants × roadmap areas, shaded by delay severity) when the network has roughly 5–25 plants — below that it's unreadable-sparse, above it it's unreadable-dense. For very small or very large networks, stick with the ranked list.

## What not to do

- Don't call `find_bottlenecks` without a `plant` argument expecting a network-wide answer — it doesn't do that.
- Don't just report "X is stalled" with no suggested action — the point of this skill is triage, not just a status readout.
