---
summary: 'Coding conventions for this project.'
read_when:
  - Writing new code.
  - Reviewing a pull request.
---

# Style

Adapt the sections below to your project's language and toolchain.

## Formatting

- All code must pass the project formatter. No exceptions.
- All code must pass the project linter. No exceptions.

## Naming

<!-- Replace with project-specific naming conventions. Example: -->
- **Files:** lowercase with hyphens or underscores per language convention
- **Functions:** language-idiomatic casing
- **Types/Classes:** PascalCase
- **Constants:** SCREAMING_SNAKE_CASE

## Error Handling

<!-- Replace with project-specific error strategy. Example: -->
- Return errors, don't swallow them
- Provide context with error messages
- Don't panic/crash except in tests

## File Size

- Keep files under ~500 LOC. Split/refactor when approaching the limit.

## Project Layout

<!-- Replace with project-specific directory structure. Example: -->
- `src/` — source code
- `tests/` — test files

## Imports / Dependencies

<!-- Replace with project-specific import conventions. Example: -->
- Group imports: stdlib, external, internal
- Separate groups with blank lines

## Testing

- Tests live alongside source or in dedicated test directories
- Use descriptive test names
- Add regression tests for bugs

## Comments

- Don't over-comment obvious code
- Do comment: public API, non-obvious algorithms, edge case handling
