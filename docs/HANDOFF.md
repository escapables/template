---
summary: 'Ephemeral per-session handoff state for cross-agent pickup.'
read_when:
  - Starting a new session.
  - Picking up where a previous agent left off.
---

# Handoff

## Session
(date) — branch `main` — initial setup.

## Completed
- (none yet)

## Verification Run
- N/A

## Open Risks / Blockers
- Verification commands in workflow docs need project-specific toolchain commands.

## Next Actions
- Adapt CLAUDE.md, AGENTS.md, and skills to this project's language/toolchain.
- Populate docs/TODO.md with initial tasks.

<!--
FORMAT REFERENCE (enforced by docs/WORKFLOW.md contract):

- Max 60 total lines including front matter
- Replace stale content each session — do not accumulate history
- Keep these exact sections: Session, Completed, Verification Run,
  Open Risks / Blockers, Next Actions
- Completed: max 4 bullets (short session deltas only)
- Verification Run: concrete commands + pass/fail results
- Next Actions: 2-3 bullets with concrete directives for next agent

When coding agent wraps up, add an Approval Request describing
code changes needing reviewer sign-off.
-->
