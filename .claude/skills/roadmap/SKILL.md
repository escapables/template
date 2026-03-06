---
name: roadmap
description: Add a feature to a milestone in PRIMARY_TODO.md. Usage: /roadmap <milestone> <feature description>
---

# Roadmap

Add a feature item to a milestone in `docs/PRIMARY_TODO.md`.

## Input

The user provides a milestone identifier and a feature description. Examples:

- `/roadmap v0.4 Language toggle between swedish/english in settings`
- `/roadmap v0.5 Stream export pages to reduce memory`
- `/roadmap new v0.6 Plugin System — support for user plugins`

Use `new` before the version to create a new milestone.

## Steps

1. **Read** `docs/PRIMARY_TODO.md`.

2. **Find the target milestone** by version number (e.g., `v0.4`). If `new` was specified, create a new `## NOT DONE vX.Y Description` section with an empty table.

3. **Generate a table row** with three columns:

   | Column | How to fill |
   |--------|-------------|
   | **What** | Short noun-phrase describing the deliverable |
   | **Result** | Observable outcome when done (user-visible behavior or measurable state) |
   | **Coding tips** | Implementation hints for the coding agent — enough to start, not a full spec |

4. **Append the row** to the milestone's table.

5. **Show the user** the added row for confirmation.

## Rules

- Never modify existing rows — append only.
- Never mark items DONE — that's the coding agent + reviewer workflow.
- If the milestone doesn't exist and `new` wasn't specified, ask the user.
- Keep each column concise — one sentence or phrase. The table format enforced by `bin/validate-docs` requires `What | Result | Coding tips`.
- Coding tips should give the coding agent a starting direction without dictating exact implementation steps.
