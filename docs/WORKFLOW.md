---
summary: 'Unified pickup/handoff workflow and execution checklist for cross-agent continuity.'
read_when:
  - Starting a session.
  - Handing off work.
  - Reviewing cross-agent continuity expectations.
---

# Workflow

`HANDOFF.md` is a short continuity snapshot for cross-agent pickup.

## Handoff Contract

- Coding agent may complete up to **2 TODO items** per session before requesting reviewer approval.
- Keep `docs/HANDOFF.md` under **60** total lines (including front matter).
- Replace stale content; do not accumulate long historical logs.
- Required sections: `Session`, `Completed`, `Verification Run`, `Open Risks / Blockers`, `Next Actions`.
- `Completed` — short session deltas only (max **4** bullets).
- `Verification Run` — concrete (command + result).
- `Next Actions` — **2-3** bullets with concrete commands or checks.

## Milestone Completion

When all TODO items in a milestone are DONE, reviewer's turn:
- Evaluate milestone deliverables
- Propose next TODO items or next milestone in `PRIMARY_TODO.md` and `TODO.md`
- Update `HANDOFF.md` with new directives for coding agent

## TODO Item Lifecycle

When finishing a TODO item:
- Mark `DONE` in the task title: `### 3. DONE Harden Security`
- Mark each `Done when:` step as `DONE`: `- DONE Security hardened`
- Prefix every non-empty line in the section with `#`
- Do **not** renumber the list; preserve original numbering

When adding a new TODO item:
- Append to the current list with the next sequential number
- Do **not** renumber existing items

### Example: Active TODO item

```markdown
### 3. Harden Security
Task: Implement security hardening measures.
Scope:
- Review authentication flows
- Add rate limiting
Done when:
- Authentication reviewed
- Rate limiting implemented
```

### Example: Completed TODO item

```markdown
### 3. DONE Harden Security
# Task: Implement security hardening measures.
# Scope:
# - Review authentication flows
# - Add rate limiting
# Done when:
# - DONE Authentication reviewed
# - DONE Rate limiting implemented
```

### TODO Format Rules (enforced by `bin/validate-docs`)

| Field | Rule |
|-------|------|
| Heading | `### N. Title` — sequential numbering, 2-4 word title |
| `Task:` | Exactly one sentence ending in `. ! ?` |
| `Scope:` | 2-5 dash bullets |
| `Done when:` | 1+ dash bullets |
| Order | Must be Task → Scope → Done when |
| DONE prefix | Every non-empty line starts with `#` |
