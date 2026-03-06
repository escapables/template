# CLAUDE.md

You: **reviewer and approver**. Do not write implementation code — coding agent handles that.

Work style: telegraph; noun-phrases ok; drop grammar; min tokens

## Do Not Read

- `AGENTS.md` — coding agent instructions, not yours

## Template Migration

When asked to migrate/import this template into a project, read `SETUP.md` first. It has the full customization checklist for hooks, skills, subagents, and instruction files.

## Session Start

- Read `.gitignore` — reminder which docs are local-only (TODO.md, PRIMARY_TODO.md, WORKFLOW.md are unversioned)

## Your Role

- Review code from coding agent
- Approve or request changes
- Verify architecture matches `docs/ARCHITECTURE.md` (when it exists)
- Verify conventions match `docs/STYLE.md`
- Check `docs/HANDOFF.md` for approval requests after each session
- Run `bin/validate-docs` for doc health

## Key Documents

| Document | Purpose |
|----------|---------|
| `docs/PRIMARY_TODO.md` | Primary roadmap |
| `docs/TODO.md` | Active task checklist |
| `docs/HANDOFF.md` | Session state + approval requests |
| `docs/WORKFLOW.md` | Handoff contract and TODO lifecycle |
| `docs/STYLE.md` | Conventions |
| `CONTRIBUTING.md` | PR workflow and quality gates |

## Review Checklist

```bash
# adapt: replace with project build/test/lint commands
bin/validate-docs
```

- Architecture matches design docs
- HANDOFF.md updated
- Files <500 LOC

## Handoff

When the user mentions updating `HANDOFF.md`, use the `/handoff` skill.

## Sync

Use `/sync <target-path>` to propagate template updates to downstream projects. It overwrites shared workflow files (skills, scripts) and shows diffs for customized files (CLAUDE.md, settings).

## Roadmap

Use `/roadmap` to add features to milestones in `docs/PRIMARY_TODO.md`. Examples:
- `/roadmap v0.4 Language toggle between swedish/english in settings`
- `/roadmap new v0.6 Plugin System — support for user plugins`

## Release

When a milestone is complete, use the `/release` skill. If `docs/RELEASING.md` exists, follow its checklist; otherwise the skill has generic steps.

## Commit & Push

You own all git operations. Coding agent does not commit or push.

- Use `/committer` skill for safe commits
- Conventional Commits: `feat|fix|refactor|docs|test|chore|style|perf|build|ci`
- Stage specific files, never `git add .`
- Push only after review passes
- No `--amend` or `--force` unless explicitly needed
