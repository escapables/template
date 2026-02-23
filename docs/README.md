---
summary: 'Index of project docs with recommended read order by audience.'
read_when:
  - Onboarding to this repository.
  - Looking for what to read first.
---

# Documentation Index

## By Audience

### Users (End Users)

Start here to understand and use the project:

1. `README.md` — Project overview, quick start

### Contributors (Developers)

Start here to contribute code:

1. `README.md` — Project overview
2. `CONTRIBUTING.md` — Contribution guidelines and PR workflow
3. `docs/STYLE.md` — Coding conventions

### Maintainers (Core Team)

Internal process documentation:

1. `docs/HANDOFF.md` — Current session state (ephemeral)

Agent working docs (local, unversioned): TODO.md, PRIMARY_TODO.md, WORKFLOW.md

## Doc Responsibilities

| Document | Owned By | Purpose |
|----------|----------|---------|
| `README.md` | Repository | User-facing overview and quick start |
| `CONTRIBUTING.md` | Repository | Contributor guidelines |
| `docs/STYLE.md` | Repository | Coding conventions |
| `docs/HANDOFF.md` | Agents | Ephemeral session state |
<!--
INDEX RULES (enforced by bin/validate-docs):

- Every non-local doc in docs/ must be referenced here as a backtick path
- Local-only docs (TODO.md, PRIMARY_TODO.md, WORKFLOW.md) are excluded from checks
- Do not reference docs that don't exist

When you add a new doc to docs/, add a reference here.
When you remove a doc, remove its reference.
-->
