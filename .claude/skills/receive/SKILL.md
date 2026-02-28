---
name: receive
description: Receive and review coding agent's deliverables. Use when coding agent has submitted work for approval.
---

# Receive

Receive deliverables from coding agent and review.

## Receive

1. **Read deliverables** — `docs/HANDOFF.md` Completed + Verification Run + Approval Request = what coding agent delivered. Read `docs/TODO.md` for task acceptance criteria.
2. **Understand scope** — `git diff` + `git log` to see what changed. Cross-check against TODO items claimed as done.

## Review

3. **Verify** — Run `/validate`. Compare results against coding agent's reported verification.
4. **Review code** — Check against TODO acceptance criteria, `docs/ARCHITECTURE.md`, `docs/STYLE.md`. Files <500 LOC.
5. **Verdict** — Approve or deny each change. Denied = specific fix instructions for `/handoff` Next Actions. Approved = move straight to `/handoff`

## Rules

- Doc hierarchy authoritative: ARCHITECTURE > PRIMARY_TODO > TODO > HANDOFF.
- TODO lifecycle per WORKFLOW.md (mark DONE, never renumber).
- After verdict, run `/handoff` to update docs and commit.
