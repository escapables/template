---
name: handoff
description: Update docs with review verdict and issue next directives for coding agent. Use after reviewing deliverables with /receive.
---

# Handoff

Issue review verdict, update docs, commit.

## Issue

1. **Update docs** — Doc hierarchy: ARCHITECTURE > PRIMARY_TODO > TODO > HANDOFF.
   - Update `docs/HANDOFF.md` per WORKFLOW.md contract (<60 lines, replace stale content). Sections: Session, Completed, Verification Run, Open Risks / Blockers, Next Actions.
   - **Next Actions: always concrete directives for coding agent** — Update `docs/PRIMARY_TODO.md` and `docs/TODO.md` to give coding agent instructions which 2 TODO items next and mark completed as DONE, reprioritise, or how to fix a denied approval. Never empty/vague.
   - Always make sure next two TODO items drafted for coding agent. Never put more than 2 unfinished items in TODO.

2. **Commit** — `git status`:
   - **Docs-only:** most docs are gitignored (`HANDOFF.md`, `TODO.md`, `PRIMARY_TODO.md`, `WORKFLOW.md`). Run `bin/validate-docs` but skip commit — nothing to stage.
   - **Code + docs:** Summarise: code approval status, HANDOFF updates, other doc changes. Commit code changes with `/committer` and output to user. Single commit. No push.

## Rules

- HANDOFF.md always updated, even if nothing else changed.
- Never push — `/committer` handles commit only; push hook blocks it structurally.
- Doc hierarchy authoritative: ARCHITECTURE > PRIMARY_TODO > TODO > HANDOFF.
- TODO lifecycle per WORKFLOW.md (never renumber list unless instructed).
- `bin/validate-docs` must pass before any doc commit.
- Next Actions must give coding agent a clear next move.
