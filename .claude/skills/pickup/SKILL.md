---
name: pickup
description: Rehydrate context when starting work. Use when picking up work, starting a task, getting context, or resuming work.
---

# Pickup

Rehydrate context, determine turn, suggest next command.

## Gather

1. **Docs discovery** — `node scripts/docs-list.mjs`; honor `read_when` hints.
2. **Work-order state** — `docs/HANDOFF.md`: who acted last, what delivered, what pending.
3. **TODO** — `docs/TODO.md` for current task + acceptance criteria.
4. **Architecture** — `docs/ARCHITECTURE.md` if reviewing design decisions.
5. **Roadmap** — `docs/PRIMARY_TODO.md` for milestone context.
6. **Repo state** — `git status -sb`; local commits not pushed, uncommitted work.
7. **CI/PR** — if PR exists: `gh pr view --comments --files`.

## Determine Turn

8. **Read HANDOFF.md sections:**
   - Approval Request present → **reviewer's turn**. Coding agent delivered, waiting for review.
   - Next Actions with coding directives → **coding agent's turn**.
   - Ambiguous / stale → flag it. Ask user or suggest `/handoff` to reset.

## Output

Concise bullets:
- Branch + working directory state
- PR/issue status (if any)
- Failing checks (if any)
- Current TODO item
- Whose turn + why

Then suggest the appropriate next command:
- **Your turn** → suggest `/receive` to begin review.
- **Not your turn** → summarise what's waiting. No action beyond summary.

Do not execute `/receive` or `/handoff` automatically — wait for user permission.
