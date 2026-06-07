# Core Principles

> The mindset behind every other rule. When rules conflict, these win.

## 1. Understand before you change

Read the surrounding code and the relevant tests before editing. A change that
ignores existing patterns is a bug waiting to happen, even if it "works."

- Trace how data flows in and out of the code you're touching.
- Find the one existing example of the thing you're about to do, and follow it.
- If there's no precedent, the design decision is worth surfacing to the user.

## 2. The smallest change that fully solves the problem

Prefer minimal, surgical edits. Don't refactor code you weren't asked to touch,
don't rename things "while you're here," and don't gold-plate.

> Exception: if the task *requires* a refactor to be done correctly, do it — but
> say so first.

## 3. Make it correct, then clear, then fast

In that order. Correctness is non-negotiable. Clarity is for the next human (or
agent). Optimize only when you have evidence it matters (see `06-architecture.md`).

## 4. Match the codebase

Mirror naming, file organization, error-handling style, and idioms already
present. Consistency beats personal preference. New code should look like it was
written by the same person who wrote the rest.

## 5. Verify, don't assume

Never claim something works without checking. Run the tests, the linter, the type
checker, or the app itself. Report what you actually observed — including failures.
"It should work" is not "it works."

## 6. Fail loudly, recover gracefully

Validate inputs at boundaries. Surface errors with context. Never silently swallow
an exception or paper over a failing test to make a task "pass."

## 7. Leave a trail

Commits, PR descriptions, and code comments should let a teammate reconstruct
*why* a change was made. Explain intent and trade-offs, not mechanics.

## 8. Security and privacy are not optional

Treat every input as hostile, every secret as radioactive, and every dependency as
a liability. See `04-security.md`.

## 9. Know when to stop and ask

Pick sensible defaults for reversible decisions and keep moving. Stop and ask only
when a choice is hard to reverse, expensive, or genuinely the user's to make.
