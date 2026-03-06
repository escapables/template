# Agent Workflow Template

A two-agent development workflow template with structured handoff, review gating, and automation.

## What This Is

A ready-to-clone project skeleton for teams using a **reviewer + coding agent** model:

- **Reviewer** (Claude Code) — reviews, approves, commits, pushes, releases
- **Coding agent** (Codex or similar) — writes code, tests, debugs; does not commit

The template provides the handoff contract, doc infrastructure, skills, hooks, and subagents to make this workflow repeatable across projects.

## Quick Start

1. Copy this template into your project root
2. Read `SETUP.md` for the migration checklist
3. Customize hooks, skills, and instruction files for your stack
4. Uncomment the relevant `.gitignore` lines for your project type

## What's Included

### Instruction Files

| File | Audience | Purpose |
|------|----------|---------|
| `CLAUDE.md` | Reviewer | Review, approve, commit, release |
| `AGENTS.md` | Coding agent | Implement, test, hand off |
| `SETUP.md` | Either | Migration/customization checklist |
| `CONTRIBUTING.md` | Contributors | PR workflow and quality gates |

### Doc Infrastructure

| File | Purpose |
|------|---------|
| `docs/PRIMARY_TODO.md` | Implementation roadmap by milestone |
| `docs/TODO.md` | Active task checklist (max 2 items) |
| `docs/HANDOFF.md` | Ephemeral session state between agents |
| `docs/WORKFLOW.md` | Handoff contract and TODO lifecycle |
| `docs/STYLE.md` | Coding conventions (fill per project) |
| `docs/README.md` | Doc index with read-when hints |

### Automations

| Type | Location | What |
|------|----------|------|
| **Hooks** | `.claude/settings.json` | Auto-format on edit (Python/Go/Rust/JS/TS), lock file guard |
| **Skills** | `.claude/skills/` | pickup, handoff, receive, committer, release, roadmap, sync, docs-list, fixissue, guardrails |
| **Skills** | `.agents/skills/` | pickup, handoff, receive |
| **Subagents** | `.agents/agents/` | tdd-guide (test-driven development enforcer) |

### Scripts

| Script | Purpose |
|--------|---------|
| `bin/validate-docs` | Markdown validation and doc index checks |
| `scripts/docs-list.mjs` | Doc discovery with read-when hints |

## Workflow Overview

```
Coding agent                    Reviewer
─────────────                   ────────
/pickup                         /pickup
  ↓                               ↓
implement TODO items            /receive (review deliverables)
  ↓                               ↓
update HANDOFF.md               approve or deny
  (approval request)              ↓
                                /handoff (update docs, commit)
                                  ↓
                                /release (when milestone done)
```

### Planning Shortcuts

Add features to milestones without manual doc editing:

```
/roadmap v0.4 Language toggle between swedish/english in settings
/roadmap new v0.6 Plugin System — support for user plugins
```

This appends a properly formatted row to the milestone table in `docs/PRIMARY_TODO.md`.

### Template Sync

Propagate template updates to downstream projects:

```
/sync ~/projects/my-app
```

Overwrites shared workflow files (skills, scripts, subagents) and shows diffs for customized files (CLAUDE.md, settings.json) so you can merge selectively.

## License

GPL-3.0 — see `LICENSE`.
