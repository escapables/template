# Template Setup

This repository is a workorder/handoff system template for two-agent development (reviewer + coding agent). When migrating it into a new project, customize these files to match the target project's stack.

## Migration Checklist

### 1. Hooks (`.claude/settings.json`)

The PostToolUse hook auto-formats files after edits. It supports Python, Go, Rust, and JS/TS out of the box. **Customize:**

- Remove formatters for languages not used in the project
- Add project-specific formatters (e.g., `black` instead of `ruff`, `clang-format` for C/C++)
- Adjust the PreToolUse lock guard if the project has additional generated files to protect

### 2. Subagents (`.agents/agents/`)

- `tdd-guide.md` — Update to reference the project's test framework and conventions
  - Set the specific test runner (pytest, go test, jest, cargo test, etc.)
  - Set the coverage minimum if the project has one
  - Note any project-specific test patterns (table-driven, fixtures, factories)

### 3. Skills

#### Reviewer (`.claude/skills/`)

- `release/SKILL.md` — If the project has `docs/RELEASING.md`, the skill defers to it. Otherwise:
  - Replace the generic gate command with the project's actual gate (e.g., `./bin/test-gate`)
  - Add project-specific release steps (portable builds, artifact uploads, deploy)
  - Set the correct default branch name if not `main`

#### Coding agent (`.agents/skills/`)

- `pickup`, `handoff`, `receive` — Generally work as-is. Update if the project uses different doc paths.

### 4. Instruction files

- `CLAUDE.md` — Replace `# adapt:` comments with actual project commands (test gate, build)
- `AGENTS.md` — Replace `# adapt:` comments. Fill in Project Context section (goal, stack, conventions)
- `CONTRIBUTING.md` — Replace `# adapt:` placeholders with real build/test/lint commands
- `docs/STYLE.md` — Write project-specific conventions

### 5. Doc infrastructure

- `bin/validate-docs` — Works as-is for markdown validation
- `docs/PRIMARY_TODO.md` — Populate with the project's initial roadmap milestones
- `docs/TODO.md` — Draft the first 2 TODO items for the coding agent
- `docs/HANDOFF.md` — Reset to empty session state

## What NOT to change

- The two-agent boundary (reviewer vs coding agent) — this is structural
- The handoff contract in `docs/WORKFLOW.md`
- The TODO lifecycle (mark DONE, never renumber)
- The doc hierarchy (PRODUCT_REQUIREMENTS > PRIMARY_TODO > TODO > HANDOFF)
