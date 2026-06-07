---
name: refactor-safely
description: Improve code structure without changing behavior, guarded by tests. Use when the user wants to clean up, restructure, simplify, or pay down tech debt.
---

# Refactor Safely

Refactoring changes structure, not behavior. The safety net is tests.

## 1. Establish the net

- Ensure the code under refactor has tests that pin its current behavior. If
  coverage is thin, **add characterization tests first** so you can detect any
  behavior change.
- Run them — they must be green before you start.

## 2. Scope it

- Define exactly what you're improving and why (readability, duplication, coupling,
  performance). Keep the scope tight; resist expanding.
- Don't mix refactoring with feature changes or bug fixes — separate commits.

## 3. Refactor in small steps

- Make one transformation at a time (extract function, rename, inline, split module).
- Run the tests after each step. If they go red, you just learned the step changed
  behavior — revert and reconsider.
- Lean on automated refactorings (IDE rename, extract) where available; they're safer.

## 4. Improve toward the heuristics

- Apply `rules/06-architecture.md`: reduce coupling, raise cohesion, remove the wrong
  abstraction, simplify control flow.
- Delete dead code. Don't leave commented-out blocks.

## 5. Verify behavior is unchanged

- Full suite, lint, types all green. Diff should show structure changing, not
  outputs. If a test had to change, that's a behavior change — flag it explicitly.

## 6. Summarize

- State what improved and confirm behavior is identical. Note measurable wins
  (less duplication, fewer params, faster path) where relevant.
