# Code Quality Checklist

Assess the change for correctness, clarity, and maintainability. Pairs with
`rules/00-core-principles.md`, `01-code-style.md`, and `06-architecture.md`.

## Correctness
- [ ] Logic is right for the happy path and the edge cases
- [ ] Null/undefined/empty/zero/max boundaries handled
- [ ] Errors are caught at the right layer and surfaced with context
- [ ] No race conditions or unguarded shared mutable state
- [ ] No off-by-one, wrong operator, or inverted-condition bugs

## Clarity & style
- [ ] Names clearly express intent
- [ ] Functions are small and do one thing
- [ ] Control flow is shallow (guard clauses over deep nesting)
- [ ] No dead code, commented-out blocks, or stray debug logging
- [ ] Comments explain *why*, not *what*
- [ ] Consistent with surrounding code and project conventions

## Design
- [ ] Concerns are separated (logic vs. I/O vs. presentation)
- [ ] No premature/wrong abstraction; duplication is intentional or removed
- [ ] Dependencies point the right direction (toward abstractions)
- [ ] Single source of truth for state/config — no drifting duplicates
- [ ] Change is appropriately scoped — no unrelated drive-by edits

## Tests
- [ ] New/changed behavior is covered by tests
- [ ] Edge cases and failure modes tested
- [ ] Tests are deterministic and independent
- [ ] No tests skipped/deleted to force a green build

## Robustness
- [ ] Inputs validated at boundaries
- [ ] Resources (files, connections, locks) released reliably
- [ ] Sensible defaults; fails loudly rather than silently

## Verification
- [ ] Lint passes
- [ ] Type check passes
- [ ] Full relevant test suite passes (with actual output reviewed)

## Notes
-
