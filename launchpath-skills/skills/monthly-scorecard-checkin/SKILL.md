---
name: monthly-scorecard-checkin
description: Use when a planter wants to do their MONTHLY scorecard check-in — "let's do my monthly check-in", "time for our scorecard", "record this month's numbers", "we had 24 gospel conversations", "log our baptisms for August", "review last month's commitments", "what did we commit to this month". Requires get_scorecard, record_vital_actuals, set_faithful_action_outcome, commit_faithful_action, and submit_scorecard_checkin. Writer-only (planter/team_member) on licensed plants — see the permission note. Do not use for the WEEKLY task walkthrough (weekly-check-in) or a read-only look at the numbers (vitals-review).
---

# Monthly Scorecard Check-in

The monthly rhythm, not the weekly one. `weekly-check-in` walks roadmap **tasks**; this walks the **scorecard** — the numbers a plant prays over and the commitments its team made. Both write, and they don't overlap: if the user says "check-in" without saying which, ask.

## The vocabulary matters

- **Key vitals** are lag measures — gospel conversations, baptisms, launch team size. They're God's work. Report them; never congratulate or scold a team for them.
- **Faithful actions** are lead measures — what the team said they would *do* this month. These are the team's responsibility, and it's fair to ask directly whether they happened.

Keep that distinction in the language. "You're behind on baptisms" is the wrong sentence. "Baptisms came in under the goal — worth bringing to prayer" is the right one.

## Permission note

Recording actuals, committing actions, and submitting the check-in require the `planter` or `team_member` role on a plant with an active license. Coaches are read-only by design. If a call returns "read-only" or "license required", relay which one it was and stop — don't retry or route around it.

## Tools

- `get_scorecard(plant, month?)` — always start here. Shows the vision statement, each vital with its goal and recent trend, this month's faithful actions, last month's (with outcomes), and whether the check-in is in.
- `record_vital_actuals(entries, plant?, month?)` — the month's real numbers. Pass a vital name fragment; it resolves. Several vitals in one call is fine and preferred.
- `set_faithful_action_outcome(task, status?, outcome?)` — last month's review: complete or skip, plus a sentence on what came of it. The outcome note is the part worth the most later — press gently for it.
- `commit_faithful_action(title, plant?, assignee?, month?)` — next month's commitments. **Pass `month` explicitly** (e.g. "next month") when committing forward; it defaults to the current month.
- `submit_scorecard_checkin(plant?, month?)` — closes the month out. It's what a coach and the network see. Re-submittable all month, so a check-in with a blank vital isn't a dead end.

## Workflow

Follow the app's own four steps, in order:

1. **Numbers.** `get_scorecard` first, then ask for each vital's actual and record them in one `record_vital_actuals` call. If the user doesn't know one, leave it blank rather than guessing — the check-in can be re-submitted later.
2. **Last month's actions.** Walk each one: did it happen? Record status and an outcome sentence via `set_faithful_action_outcome`. A skipped action is normal, not a failure — say so.
3. **Next month's actions.** Ask what the team is committing to, and to whom each belongs. Use `commit_faithful_action` with `month` set to next month and an `assignee` where the user names one.
4. **Submit.** `submit_scorecard_checkin`, then relay any vital it reports as still blank.

Close by reading the vitals back as a prayer prompt rather than a scoreboard — that's the whole theological point of the split.

## What not to do

- Don't guess or interpolate a number the user didn't give. A blank month is honest data; an invented one corrupts the trend.
- Don't skip step 2. Committing new actions without reviewing the last set is how the rhythm dies.
- Don't treat a missed goal as the team's failure, or a met goal as their achievement — the vitals are lag measures on purpose.
- Don't use `update_task_status` on a faithful action here; `set_faithful_action_outcome` records the outcome note at the same time.
