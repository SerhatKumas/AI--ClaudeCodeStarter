---
name: implement-feature
description: Plan and implement a feature end-to-end with tests and docs, following the project's rules. Use when the user asks to build/add a feature or capability rather than fix a small bug.
---

# Implement Feature

A disciplined workflow for adding a feature without breaking things. Follow the
steps in order; don't skip straight to coding.

## 1. Understand the request

- Restate the goal in one sentence. If it's ambiguous or has hidden decisions,
  ask 1–3 sharp questions before writing code.
- Identify acceptance criteria: how will we know it's done and correct?

## 2. Explore the codebase

- Find the closest existing feature and read how it's wired (routes, services,
  data layer, tests, types).
- Note the patterns to mirror: error handling, validation, naming, file layout.
- List the files you'll likely create or change.

## 3. Plan

- Sketch the change as a short ordered list of edits.
- Call out anything risky or hard to reverse (schema change, new dependency, public
  API change) and confirm with the user first. Record big decisions as an ADR
  (`templates/adr-template.md`).

## 4. Implement

- Make the smallest set of changes that fully satisfies the criteria.
- Mirror existing patterns (see `rules/01-code-style.md` and `rules/06-architecture.md`).
- Validate inputs at the boundary; handle errors at the right layer
  (`rules/04-security.md`).

## 5. Test

- Add tests covering the happy path, edges, and failures (`rules/03-testing.md`).
- For any bug uncovered, add a regression test.

## 6. Verify

- Run the test suite, linter, and type checker. Fix what you broke.
- If there's a runnable app, exercise the feature and confirm the behavior.

## 7. Document & summarize

- Update README/docs/env examples if behavior or setup changed
  (`rules/05-documentation.md`).
- Summarize what changed, why, how to test, and any follow-ups. Do **not** commit
  unless asked.
