---
name: fixissue
description: Fix an issue end-to-end with tests and handoff. Use when fixing a bug or resolving a problem report.
---

# Fix Issue

End-to-end issue resolution for the coding agent.

## Workflow

1. **Understand** — read the issue; reproduce if possible; find root cause
2. **Fix** — fix root cause, not symptoms; refactor if needed
3. **Test** — add regression test that fails before fix, passes after; run full suite
4. **Verify** — build + lint + docs:
   ```bash
   bin/validate-docs
   ```
5. **Hand off** — update `docs/HANDOFF.md` with what changed and leave approval request for reviewer. Do not commit.

## Checklist

- [ ] Root cause fixed (not band-aid)
- [ ] Regression test added + passing
- [ ] Build clean
- [ ] HANDOFF.md updated with approval request
- [ ] Do NOT commit, push, or close the issue — reviewer handles that
