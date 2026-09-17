---
name: network-scorecard-review
description: Use when a network admin or coach asks about VITALS or CHECK-INS across plants — "how are vitals across the network", "who hasn't checked in this month", "show me the network scorecard", "which plants are missing their numbers", "how did the network do in July", "baptisms across our plants". Requires network_scorecard, plus get_scorecard to drill into one plant. Do not use for task progress or stalled plants (network-health-dashboard, stalled-plant-alert) or a single planter's own numbers (vitals-review).
---

# Network Scorecard Review

The vitals side of the network view. `network-health-dashboard` answers "who's behind on their roadmap"; this answers "what's actually happening in these churches, and who hasn't reported."

## Tools

- `network_scorecard(network?, month?)` — every plant the caller can see in a network, each plant's numbers against the network's shared vitals, and whether the month's check-in is in. Already ordered worst-first and ends with a nudge list. Pass `network` only when the account belongs to more than one; pass `month` for a past month.
- `get_scorecard(plant, month?)` — drill into one plant, including its own vitals beyond the network's shared set and its faithful actions.

## Two audiences, one tool

An org admin gets every plant in the network; a coach gets only the plants they coach — the same call, scoped by the database. Read the tool's own header line ("Showing the plants you coach") and frame the response to match. Don't tell a coach this is the whole network.

## The paid tier

The vitals rollup requires the network's Network Pro subscription; check-in status is always visible. If the tool reports the rollup is a Pro feature, relay that once, plainly, and give the user everything that *is* available — who has and hasn't checked in is genuinely useful on its own. Don't pitch, and don't repeat the upgrade line in follow-up answers.

## Workflow

1. Call `network_scorecard`. Lead with the check-in count ("3 of 5 plants have submitted August"), because a missing check-in is the most actionable thing in the response.
2. Walk the plants in the order returned. For each, report the numbers against goal in the tool's own words — **ahead, close, behind** — which are the same words the planter sees in the app; don't sharpen them. Where a plant is behind on a shared vital, note it without editorializing about the planter.
3. Close with the nudge list — the plants that still owe a check-in. Frame it as a follow-up, not a compliance report: a missed check-in is usually a busy month.
4. Drill into a single plant with `get_scorecard` only when asked, or when one plant is clearly the reason the network's picture looks the way it does.

If the user's question is really about blocked tasks or stalled plants, hand off to `stalled-plant-alert` rather than answering it from vitals data.

## Artifact

A grid: plants down the side, network vitals across the top, actual-over-goal in each cell with a green/amber/red/grey treatment, and a final column for check-in status. Grey means nothing was recorded — keep it visually distinct from red, which means recorded and below goal. A plant with no data still gets a full row; the silence is the signal.

## What not to do

- Don't average plants into a single network number — one strong plant will hide four quiet ones.
- Don't treat grey as failing, in the grid or in the prose.
- Don't call `get_scorecard` on every plant to assemble your own rollup; `network_scorecard` is one call and respects the paid gate.
- Don't name a plant as "not participating" — report only that the check-in hasn't come in yet.
