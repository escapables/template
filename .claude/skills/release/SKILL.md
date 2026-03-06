---
name: release
description: Run the full release checklist — changelog, commit, tag, push branch + tag.
---

# Release

Create a versioned release. Adapt steps to the project's release process.

## Inputs

The user provides the version number (e.g., `v1.2.0`). If omitted, determine from `docs/PRIMARY_TODO.md` milestone status.

## Steps

1. **Gate** — Run the project's test/lint gate. Stop if it fails.

2. **Changelog** — Read `CHANGELOG.md`. If it exists, curate `## Unreleased` bullets into `## [X.Y.Z] - YYYY-MM-DD`. Keep a fresh empty `## Unreleased` at top. Only user-visible changes (feature/fix/regression/perf). If `CHANGELOG.md` is missing, create it.

3. **Commit** — Stage `CHANGELOG.md` and commit: `chore: release vX.Y.Z`.

4. **Tag** — `git tag vX.Y.Z` on the release commit.

5. **Verify tag** — `git show --no-patch --decorate vX.Y.Z` to confirm placement.

6. **Push** — Push **both** branch and tag in sequence:
   ```bash
   git push origin <branch>
   git push origin vX.Y.Z
   ```
   Tags must be pushed separately — `git push` alone does not push tags.

7. **Confirm CI** — `gh run list --limit 3` to verify the tag triggered CI (if configured).

8. **Update HANDOFF** — Record release SHA/tag + gate outcome in `docs/HANDOFF.md`.

## Rules

- Reviewer owns all git operations — this skill is reviewer-only.
- Always push the tag explicitly — forgetting this is a common mistake.
- Do not amend or force-push.
- If `docs/RELEASING.md` exists in the project, follow its checklist instead of these generic steps.
