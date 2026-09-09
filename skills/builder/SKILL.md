---
name: builder
description: Implementation workflow for coding work. Always use whenever you are implementing, building, writing, or changing code: features, bug fixes, refactors, and test changes. It delegates each task to the builder subagent, reviews the result with the reviewer subagent, loops until no important issues remain, and then produces a final report including any decisions recorded.
---

# Builder Workflow

You run this workflow whenever you implement code. It applies to all
implementation work: features, bug fixes, refactors, and test changes.

## Before you start

Take the given context as the plan. This can be a single task, a list of
tasks, a spec, a design, or a request. Turn it into an ordered list of
tasks. Keep the plan explicit: each task has a clear goal and a clear
definition of done.

If a task is too large to review in one pass, split it before you start.

## For each task

Repeat these steps for every task in order.

1. Spawn the `builder` subagent with the full task context. Give it the
   task, the plan it comes from, and any project conventions it must
   follow. Tell it to report what it changed and how it verified the work.

2. Spawn the `reviewer` subagent on the result. Give it the diff or the
   changed files. Ask it to report findings.

3. Triage the findings. An important issue is a defect, a break with
   project conventions, or a deviation from the plan. Send every important
   issue back to `builder` to fix. Minor preferences can be skipped, but
   name them in the report.

4. Loop. After `builder` fixes the issues, review again. Keep going until
   the reviewer finds no important issues. Cap the loop at three rounds. If
   an important issue survives the cap, mark it as not fixed and move on.

5. Move to the next task.

## Keep a ledger

While you work, keep a record per task:

- the task
- what `builder` changed
- what `reviewer` found
- which findings were fixed, and how
- which findings could not be fixed, and why
- any deviation from the plan

## Record decisions

When the work settles a decision the project should remember, follow the
project's convention for recording decisions. Look for an ADR directory
(`docs/adr/`), a decision log, or a mention in AGENTS.md or CLAUDE.md. If
a convention exists, follow it. If the project has the `adr` skill, use
it. If no convention exists, do not create one.

## Final report

When all tasks are done, present one report:

- the list of tasks and their status
- for each task, what review caught and what was fixed
- anything that could not be fixed, and why
- every deviation from the original plan, stated plainly
- the decisions recorded, if any
