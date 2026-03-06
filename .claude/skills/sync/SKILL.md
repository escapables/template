---
name: sync
description: Propagate template updates to a downstream project. Usage: /sync <target-project-path>
---

# Sync

Compare this template against a downstream project and selectively apply updates.

## Input

The user provides the target project path. Example:

- `/sync ~/projects/affisch2`

## File Categories

### Verbatim sync (overwrite without asking)

These are workflow infrastructure — identical across projects:

- `.claude/skills/*/SKILL.md` (all skills)
- `.agents/skills/*/SKILL.md` (all skills)
- `.agents/agents/*.md` (all subagents)
- `bin/validate-docs`
- `scripts/docs-list.mjs`
- `docs/WORKFLOW.md`
- `CONTRIBUTING.md`
- `SETUP.md`

### Diff-only (show changes, ask before applying)

These are customized per-project — never blindly overwrite:

- `CLAUDE.md`
- `AGENTS.md`
- `.claude/settings.json`
- `.gitignore`
- `docs/STYLE.md`
- `docs/README.md`

### Skip (never sync)

These are project-specific state — never touch:

- `docs/HANDOFF.md`
- `docs/TODO.md`
- `docs/PRIMARY_TODO.md`
- `README.md`
- `LICENSE`
- Any file not present in the template

## Steps

1. **Verify target** — Confirm the target path exists and has a `.claude/` or `CLAUDE.md`.

2. **Verbatim files** — For each verbatim file:
   - If missing in target: copy it, report as `ADDED`
   - If identical: report as `OK`
   - If different: overwrite, report as `UPDATED`
   - List all changes as a summary table

3. **Diff-only files** — For each diff-only file:
   - If missing in target: show the template version, ask if user wants it copied
   - If identical: report as `OK`
   - If different: show the diff and ask user what to do (apply / skip / manual merge)

4. **Summary** — Print counts: added, updated, skipped, identical.

## Rules

- Never modify template files — this is one-way (template → target).
- Never touch files in the Skip category.
- Always show the user what changed before committing in the target project.
- If a skill exists in the target but not the template, leave it alone (it's project-specific).
