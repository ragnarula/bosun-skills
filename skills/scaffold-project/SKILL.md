---
name: scaffold-project
description: Set up the project documents that guide work in a repository. Use when the user wants to scaffold, bootstrap, or set up a project, or asks for a vision, engineering principles, code standards, a decision log, a place for proposals and designs, a place for work in progress, or an index of where these live. It checks what already exists, interviews the user about where each item goes and what it says, offering a simple suggestion for each, and then writes the files and the index.
---

# Scaffold Project

You make sure a project has a known place for each of these items:

1. **Vision**: what the project is for, who it serves, and what it will not do.
2. **Engineering principles**: the values that guide trade-offs.
3. **Code standards**: conventions, best practices, and guidelines for code.
4. **Decision records**: a way to record decisions as implementation goes on.
5. **Proposals and designs**: a place for upcoming work before it starts.
6. **Work in progress**: a place for work that has started and is not done.
7. **Index**: one file that says where all of the above lives.

The user decides where each item lives and what it says. Your job is to
offer a simple starting point and write down what they choose.

## Step 1: Survey the project

Before you ask anything, look at what exists. Check for:

- `README.md`, `CLAUDE.md`, `AGENTS.md`, `CONTRIBUTING.md`
- a `docs/` directory and anything that looks like a vision, principles,
  standards, ADRs, RFCs, proposals, designs, or plans
- linter and formatter configs, which imply code standards
- the languages, frameworks, and layout of the code

Read what you find. For each of the seven items, note whether it already
exists, where, and whether it is complete enough to keep.

## Step 2: Interview the user

Go through the items in order, one or two at a time. For each item:

- If it already exists, say where. Ask whether to keep it, change it, or
  move it. Do not rewrite content the user wants to keep.
- If it is missing, offer the suggested location and a short draft of
  the initial content. Base the draft on what you learned in Step 1, not
  on generic filler.
- Ask the user to accept, change the location, change the content, or
  skip the item.

Use the AskUserQuestion tool where it is available. Put the suggestion
first and mark it as recommended. The user can always give their own
answer.

Keep drafts short. A few lines that the user agrees with are better than
a page they have to edit. The documents can grow later.

For the vision, ask the user what the project is for before you draft it.
You cannot infer a vision from code alone. Offer a draft based on the
README if one exists.

### Suggested defaults

Offer these unless the project already has a convention.

| Item | Location | Initial content |
| --- | --- | --- |
| Vision | `docs/vision.md` | One paragraph on the purpose. A short list of goals. A short list of non-goals. |
| Engineering principles | `docs/principles.md` | Three to five principles, each one line with a short reason. Draw them from the user's answers. |
| Code standards | `docs/standards.md` | Language and tooling, formatting and linting (point to the configs), naming, error handling, testing, and review expectations. One or two lines each. |
| Decision records | `docs/decisions.md` | A minimal append-only log. A one-line intro, then one entry per decision: `## YYYY-MM-DD: Title`, followed by the decision, the reason, and the milestone it came from, if any. Newest entry last. |
| Proposals and designs | `docs/milestones/<name>/` | One folder per milestone. It holds whatever documents the work needs, such as `proposal.md`, `design.md`, `research.md`, and `tasks.md`. No fixed set of files. |
| Work in progress | `docs/milestones/README.md` | A list of milestones, each with its folder and a status: proposed, in progress, or done. |
| Index | `CLAUDE.md` | A short section that lists each item and its path, and says how they relate. Link to it from `README.md`. |

Proposals and work in progress share one location by default. A milestone
folder is created when the work is proposed and stays in place as the work
moves forward. Only its status in `docs/milestones/README.md` changes.

Do not create example milestone folders or empty template files. Create
`docs/milestones/README.md` with an empty list, unless the user names
work that is already planned or in progress.

### How the items relate

Explain this flow to the user when you set up items 4 to 6, so the
locations make sense together:

- Upcoming work gets a folder under `docs/milestones/` and status
  proposed. Its proposal, research, and design go in that folder.
- When work starts, its status changes to in progress. Its tasks and
  notes go in the same folder.
- Decisions made along the way are appended to `docs/decisions.md`, with
  a link to the milestone.
- When work is done, its status changes to done. The folder stays as a
  record.

Ask whether the user wants this flow or a different one, and write their
answer into the index.

## Step 3: Confirm the plan

Before you write anything, show a summary: each item, its location, and
whether you will create, change, or keep it. Ask the user to confirm.

## Step 4: Write the files

- Create the files and directories the user agreed to.
- Do not overwrite existing content without the user's agreement.
- Write the index last, so it lists the final paths.
- If the index is `CLAUDE.md` and it already exists, add a section to it.
  Do not replace the file.
- Do not commit unless the user asks.

## Final report

Tell the user:

- each item and where it lives
- which files you created, changed, or kept
- any item the user skipped
- the next step for any item that still needs real content, such as a
  vision with only a draft paragraph
