---
name: receive
description: Receive work order from reviewer and execute. Use at session start as well to pick up directives.
---

# Receive

Receive directives from reviewer and execute.

## Receive

1. **Read work order** — `docs/HANDOFF.md` Next Actions section = your directives. Read `docs/TODO.md` for task details.
2. **Check turn** — If HANDOFF.md has an Approval Request or Next Actions directed at the reviewer (not coding agent), STOP. Summarise: "Reviewer's turn — waiting on approval." Do not execute.
3. **Understand scope** — Reviewer verdict, required fixes, which TODO to pick up. If unclear, check `docs/PRIMARY_TODO.md` for milestone context.
4. **Execute** — Implement per directives. Follow ARCHITECTURE.md + STYLE.md conventions.

## Rules

- Doc hierarchy authoritative: ARCHITECTURE > PRIMARY_TODO > TODO > HANDOFF.
- Never commit, push, or approve own work — leave for reviewer.
- After implementation, run `$handoff` to wrap up session.
