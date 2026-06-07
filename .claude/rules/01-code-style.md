# Code Style

> Defer to the project's existing formatter/linter config. This document covers
> judgment calls that tools can't enforce. Delete the language sections you don't use.

## Universal

- **Names describe intent.** `userCount`, not `n`. `isExpired`, not `flag`. A good
  name removes the need for a comment.
- **Functions do one thing.** If you need "and" to describe it, split it.
- **Keep nesting shallow.** Prefer early returns / guard clauses over deep `if/else`.
- **No dead code.** Delete commented-out blocks and unused vars — git remembers.
- **Comments explain *why*, not *what*.** The code already says what. Reserve
  comments for intent, edge cases, and non-obvious trade-offs.
- **Constants over magic values.** Name the `3600`, the `"prod"`, the `0.05`.
- **Handle errors at the right layer.** Don't catch what you can't meaningfully handle.
- **Pure where possible.** Isolate side effects (I/O, network, globals) from logic.

## Formatting

Let the formatter own whitespace, quotes, and line length. Never hand-format or
argue with the tool. If there's no formatter configured, add one — don't invent a
personal style.

## TypeScript / JavaScript

- Prefer `const`; avoid `let`; never `var`.
- No `any` — use `unknown` and narrow, or write the type.
- Prefer `type`/`interface` over inline shapes that repeat.
- Async: `async/await` over raw `.then()` chains; never float a promise.
- Avoid default exports for shared modules (named exports refactor better).
- Use `===` / `!==`. Use optional chaining and nullish coalescing.

## Python

- Type hints on public functions; run `mypy`/`pyright` if configured.
- Follow PEP 8 via `ruff`/`black`; f-strings over `%`/`.format()`.
- Prefer comprehensions for simple maps/filters; loops when logic grows.
- Use `pathlib` over `os.path`; context managers for resources.
- Dataclasses / Pydantic for structured data, not bare dicts.

## Go

- `gofmt`/`goimports` are law. Handle every `error`; wrap with `%w` for context.
- Accept interfaces, return structs. Keep packages small and cohesive.

## Rust

- `cargo fmt` + `clippy` clean. Prefer `Result`/`?` over `unwrap()` in non-test code.
- Make illegal states unrepresentable with the type system.

## When in doubt

Open a neighboring file and copy its conventions. The codebase is the style guide.
