---
name: development
description: Load before designing or writing anything in a project: code, tests, migrations, generated code, documentation, or proposals. It finds the project's vision, principles, standards, decision log, and milestone documents, says how to validate the work as you go, and says what to record afterwards. Use it before the work, not after. Triggers on any request to design, add, change, fix, refactor, extend, or document behaviour.
---

# Development

## Find the project documents

Read the index first. It is usually `CLAUDE.md` or `README.md`, and the
`scaffold-project` skill writes it. It says where these live:

- the vision
- the engineering principles
- the code standards
- the decision log
- the milestone documents

If there is no index, look in the default locations: `docs/vision.md`,
`docs/principles.md`, `docs/standards.md`, `docs/decisions.md`, and
`docs/milestones/`. If you still cannot find them, say so, and suggest the
`scaffold-project` skill. Do not invent conventions to fill the gap.

## Before

Read the standards that apply to what you are changing, and follow them.
If the standards are split by topic, read the ones that match the change.

Read the engineering principles and apply them while you design, not
after. Ask whether the change is needed at all, and whether its
complexity is worth what it buys. These questions are cheap to answer now
and expensive to answer once the code exists.

Read the decisions that touch what you are changing. They constrain later
work, and they carry the project's vocabulary. Use their terms, not
synonyms. If your design contradicts a decision, say so. Do not override
it silently.

If the work belongs to a milestone, read its folder: the proposal,
research, design, and tasks. Work from them. If the work does not match
them, say so before you start.

Check that the change fits the vision. If it does not, say so.

## During

Validate as you go. Use the build, type check, and lint commands that the
standards name. If they name none, use the usual commands for the
language, such as `cargo check` and `cargo clippy`, or `tsc` and the
project's linter. Do not leave validation to the end.

When the change is finished, run the tests that cover it. Use the test
commands that the standards name.

## After

Record a decision for any choice that would be hard to reverse: a wire
format, an on-disk format, a public API shape, or a constraint that later
work must respect. Also record a choice where you weighed real
alternatives and a later reader will need to know why one won. A bug fix
or a refactor does not need one. Follow the format the decision log
already uses. Give each rejected option a real reason, and state the
costs.

Never rewrite an existing decision to match what changed. It records what
was decided at the time. When a change overturns a decision, add a new
one that states what is now true and names the one it replaces. The only
edit the old entry allows is a pointer to the new one.

Update the milestone. Mark finished tasks as done in its `tasks.md`. If
the milestone is complete, set its status in the milestones list.

Update any documentation that the change makes wrong. Do not add a
description of how the code you just wrote works. The code is the source
of truth for what the system does. Documents hold what the code cannot
say: the rules, the procedures, and the reasons.
