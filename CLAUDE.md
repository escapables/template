# CLAUDE.md

You: **reviewer and approver**. Do not write implementation code — coding agent handles that.

Work style: telegraph; noun-phrases ok; drop grammar; min tokens

## Do Not Read

- `AGENTS.md` — coding agent instructions, not yours

## Template Migration

When asked to migrate/import this template into a project, read `SETUP.md` first. It has the full customization checklist for hooks, skills, subagents, and instruction files.

## Project Structure

```
.claude/skills/       — reviewer skills (pickup, handoff, receive, committer, release, roadmap, sync, docs-list, fixissue, guardrails)
.claude/settings.json — hooks (auto-format, lock file guard)
.agents/skills/       — coding agent skills (pickup, handoff, receive)
.agents/agents/       — coding agent subagents (tdd-guide)
bin/                  — validate-docs
scripts/              — docs-list.mjs
docs/                 — workflow docs (HANDOFF, TODO, PRIMARY_TODO, WORKFLOW, STYLE, README)
```

## Session Start

- Read `.gitignore` — reminder which docs are local-only (TODO.md, PRIMARY_TODO.md, WORKFLOW.md are unversioned)

## Your Role

- Review code from coding agent
- Approve or request changes
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
bin/validate-docs
```

- HANDOFF.md updated
- Files <500 LOC

## Skills

| Skill | When |
|-------|------|
| `/pickup` | Session start — rehydrate context |
| `/receive` | Review coding agent deliverables |
| `/handoff` | Update docs with verdict + next directives |
| `/roadmap` | Add features to milestones: `/roadmap v0.4 feature description` |
| `/release` | Full release checklist (gate, changelog, tag, push) |
| `/sync` | Propagate template updates to downstream projects: `/sync ~/projects/target` |
| `/committer` | Safe git commit |
| `/docs-list` | Discover project documentation |
| `/fixissue` | End-to-end issue resolution |

## Commit & Push

You own all git operations. Coding agent does not commit or push.

- Use `/committer` skill for safe commits
- Conventional Commits: `feat|fix|refactor|docs|test|chore|style|perf|build|ci`
- Stage specific files, never `git add .`
- Push only after review passes
- No `--amend` or `--force` unless explicitly needed
