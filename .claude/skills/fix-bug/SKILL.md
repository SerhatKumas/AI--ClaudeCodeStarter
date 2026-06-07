---
name: fix-bug
description: Diagnose and fix a bug methodically — reproduce, find root cause, write a failing test, fix, verify. Use when the user reports something broken or behaving incorrectly.
---

# Fix Bug

Resist the urge to patch the symptom. Find and fix the cause.

## 1. Reproduce

- Get an exact reproduction: inputs, steps, expected vs. actual behavior.
- Reproduce it yourself (a failing test, a script, or running the app). If you can't
  reproduce it, you can't confirm a fix — say so and ask for details.

## 2. Localize

- Trace from the symptom back toward the source. Read the stack trace fully.
- Use `git log`/`git blame` on the suspect lines — recent changes are prime suspects.
- Form a hypothesis about the root cause and confirm it with evidence (logs, a
  debugger, a targeted print). Don't guess-and-edit.

## 3. Write a failing test

- Capture the bug as a test that **fails now**. This proves you understand it and
  prevents regression (`rules/03-testing.md`).

## 4. Fix the root cause

- Make the minimal change that addresses the actual cause, not the symptom.
- Check for sibling bugs: the same mistake often repeats elsewhere in the codebase.

## 5. Verify

- The new test passes; the full relevant suite still passes; lint and types are clean.
- Confirm the original reproduction now behaves correctly.

## 6. Summarize

- Explain the root cause, the fix, and why it won't recur. Note any related code
  that shares the risk. Do not commit unless asked.
