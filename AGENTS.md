# AGENTS.md

You: **coding agent**. Write code, debug, test. Do not approve own work.

Work style: telegraph; noun-phrases ok; drop grammar; min tokens

## Do Not Read

- `CLAUDE.md` or `.claude` dir — reviewer instructions, not yours

## Template Migration

When asked to migrate/import this template into a project, read `SETUP.md` first. It has the full customization checklist for hooks, skills, subagents, and instruction files.

## Session Start

1. Read `.gitignore` — reminder which docs are local-only (TODO.md, PRIMARY_TODO.md, WORKFLOW.md are unversioned)
2. Run `pickup` skill or manually:
   - `docs/HANDOFF.md` — pick up last session
   - `docs/TODO.md` — current task
   - `docs/PRIMARY_TODO.md` — implementation roadmap
   - `docs/STYLE.md` — conventions
3. Run `node scripts/docs-list.mjs` — discover docs, honor `read_when` hints

## Work Loop

1. Implement up to **2 TODO items** per session before requesting approval
2. After each item: verify, mark DONE in `docs/TODO.md`
3. Verify after final item:
   ```bash
   bin/validate-docs
   ```
4. Update `docs/HANDOFF.md` — summarize all completed work, leave **approval request** for reviewer

## Rules

- Follow architecture docs and roadmap in `docs/PRIMARY_TODO.md`; flag deviations in HANDOFF.md
- Follow `docs/STYLE.md`
- **Files <500 LOC — hard limit.** `wc -l` before handoff. Over? Extract coherent subset into sibling module. Keep public API stable. Don't leave for reviewer.
- HANDOFF.md <60 lines; replace stale content
- Do not commit, push, merge, or approve own work — leave approval requests
- Blocked: document in HANDOFF.md, move to next unblocked task
- Bugs: add regression test
- Fix root cause, not band-aid

## Skills & Subagents

| Name | Type | When |
|------|------|------|
| `pickup` | skill | Session start — rehydrate context |
| `handoff` | skill | Wrap up session, prepare approval request |
| `receive` | skill | Review incoming directives from reviewer |
| `tdd-guide` | subagent | Delegate test planning before implementation |
