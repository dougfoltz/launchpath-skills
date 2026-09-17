# LaunchPath skills

16 Claude skills for church-planting networks, built on the
[LaunchPath](https://churchplantingchecklist.com) MCP server.

They cover three audiences: network admins looking across every plant, coaches
overseeing the ones assigned to them, and planters working their own roadmap.
Each skill decides which MCP tools to call and how to present what comes back —
the data itself always comes from LaunchPath, scoped by your own account.

## Install

Reference a single skill by name:

```
dougfoltz/launchpath-skills@network-scorecard-review
```

Every skill sits at `skills/<name>/SKILL.md`, and the directory name matches the
skill's `name` in frontmatter, so `@<name>` resolves for all 16.

Or add the whole set as a plugin marketplace:

```
/plugin marketplace add dougfoltz/launchpath-skills
/plugin install launchpath-skills@launchpath
```

The plugin bundles the LaunchPath MCP connector
(`https://churchplantingchecklist.com/api/mcp`), so installing it prompts you to
sign in to your Church Planting Checklist account. Everything the skills can see
is whatever that account can see — coaches stay read-only, and licensed content
stays licensed, because the database enforces it rather than the skills.

## The skills

### Network admins

- **`network-health-dashboard`** — A network admin or org-level user asks for a cross-plant view of how their church-planting network is doing
- **`network-progress-report`** — A network admin needs a formatted rollup for an external audience
- **`network-scorecard-review`** — A network admin or coach asks about VITALS or CHECK-INS across plants
- **`stalled-plant-alert`** — A network admin or coach asks specifically about blocked, stalled, or lagging plants
- **`coach-assignment-sync`** — A network admin asks about coaching coverage

### Coaches

- **`coached-plants-summary`** — A coach asks for a summary of the plants they personally oversee
- **`plant-deep-dive`** — A coach (or network admin) wants a full picture of ONE specific plant
- **`planter-action-items`** — A coach wants to know what their planters should be working on soon
- **`roster-health-check`** — Any leadership-roster question, whether asked by a coach about a plant they oversee or by a planter about their own team

### Planters

- **`launch-roadmap`** — A planter asks about their overall progress or where they stand
- **`this-weeks-focus`** — A planter asks what to work on soon
- **`task-deep-dive`** — A planter asks about one specific task
- **`weekly-check-in`** — A planter wants to walk through and update their tasks conversationally
- **`launch-date-reality-check`** — A planter asks whether their launch timeline is realistic
- **`vitals-review`** — A planter asks about their scorecard NUMBERS without wanting to change anything
- **`monthly-scorecard-checkin`** — A planter wants to do their MONTHLY scorecard check-in

## Requirements

A [Church Planting Checklist](https://churchplantingchecklist.com) account. Some
skills need more: task write-ups and team comments need an active plant licence,
and the network-wide vitals rollup needs the network's Network Pro subscription.
Where a skill hits one of those, it says so plainly rather than failing.

## Notes

Skills are the presentation layer; the 22 MCP tools do the retrieval. Only
`weekly-check-in` and `monthly-scorecard-checkin` write anything — the rest read.

Generated from `claude-plugin/` in the LaunchPath repo.
