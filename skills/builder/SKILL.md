---
name: builder
description: Implementation workflow for coding work. Always use whenever you are implementing, building, writing, or changing code: features, bug fixes, refactors, and test changes. It delegates each task to the builder subagent, reviews the result with the reviewer subagent, loops until no important issues remain, and then produces a final report including any decisions recorded.
---

# Builder Workflow

Turn the given context into an ordered list of tasks, each with a clear
goal and definition of done. Split any task too large to review in one
pass.

For each task, in order:

1. Spawn the `builder` subagent with the task and the plan it comes from.
2. Spawn the `reviewer` subagent on the result.
3. Send every important issue back to `builder`. An important issue is a
   defect, a break with project conventions, or a deviation from the
   plan. Note minor issues for the report.
4. Repeat review and fix until no important issues remain, for at most
   three rounds. Mark any issue that survives as not fixed.

The project's conventions, including how to record decisions, come from
the `development` skill.

## Final report

- each task and its status
- what review caught, and what was fixed
- what was not fixed, and why
- every deviation from the plan
- the decisions recorded
