---
name: vitals-review
description: Use when a planter asks about their scorecard NUMBERS without wanting to change anything — "how are our vitals", "are we hitting our goals", "how's our giving trending", "did baptisms go up", "show me our scorecard", "what does our vision say". Requires get_scorecard (and progress_report when the user wants the work behind the numbers). Read-only. Do not use when the user is ready to record a month (monthly-scorecard-checkin) or asking about roadmap task progress (launch-roadmap).
---

# Vitals Review

A read-only look at the plant's key vitals — the lag measures. Nothing here writes; if the conversation turns into "let's record August", switch to `monthly-scorecard-checkin`.

## Tools

- `get_scorecard(plant, month?)` — vision statement, every vital with goal vs. actual and a recent trail of months, this month's faithful actions, and check-in state. Pass `month` to look back at a specific one.
- `progress_report(plant, since_days?)` — optional second call, when the user asks *why* a number moved. It carries the same scorecard block plus the tasks completed in the window and the faithful actions that were finished, with their outcome notes.

## Workflow

Lead with the vision statement when the plant has one — the numbers mean something only underneath it. Then walk the vitals, saying for each what the number is, what the goal was, and which direction the trail is heading. Use the tool's own words — **ahead, close, behind** — rather than inventing your own; they're the same words the app shows the planter, and swapping in a harsher synonym gives them a second, worse verdict on one number. A vital marked "no data yet" means nobody has entered it, which is different from a zero — never report it as a zero.

When something is below goal, name it plainly and then frame it as a prayer item rather than a performance problem: these are measures of what God is doing, and the team's own commitments are tracked separately as faithful actions. When something is above goal, resist the urge to attribute it to the team's effort for the same reason.

If the user wants to know what the team actually *did* in the period, that's `progress_report` — completions and finished faithful actions — and it's a fair place to give the team credit.

## Artifact

A small dashboard: one tile per vital with the month's actual, the goal, and a sparkline over the recorded months. Grey out any vital with no data instead of drawing it as zero. If a vision statement exists, set it above the tiles as the heading — the layout should read vision-first, numbers-second.

## What not to do

- Don't call the write tools. If the user starts giving you this month's numbers, say you'll switch into the check-in and use `monthly-scorecard-checkin`.
- Don't render a missing number as 0, and don't average vitals into a single "scorecard score" — they're different things being counted.
- Don't reach for `network_scorecard` here; that's the multi-plant view for admins and coaches.
