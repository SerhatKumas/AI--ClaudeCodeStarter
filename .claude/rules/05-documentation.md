# Documentation

> Docs are a love letter to your future self and your teammates. Write them like
> someone has to act on them at 2am.

## Levels of documentation

1. **Self-documenting code** — the first and best layer. Good names and small
   functions remove most of the need for prose.
2. **Inline comments** — for the *why*: non-obvious trade-offs, workarounds, links to
   issues/specs. Never narrate the obvious (`i++ // increment i`).
3. **Docstrings / API docs** — on public functions, types, and modules. State
   purpose, params, return, errors, and any side effects.
4. **README / guides** — how to install, run, test, and contribute.
5. **ADRs** — record significant architectural decisions (see template below).

## Keep docs close to code

Documentation drifts when it lives far from what it describes. Prefer docstrings
and `README.md`s next to the code over a separate wiki that nobody updates.

## When you change behavior, change the docs

A PR that alters an API, a command, an env var, or a setup step must update the
docs in the same change. Stale docs are worse than none.

## READMEs should answer

- What is this and why does it exist?
- How do I install and run it? (copy-pasteable commands)
- How do I run the tests?
- How is it structured? (the 30-second tour)
- How do I contribute / who owns it?

## Architecture Decision Records (ADRs)

For decisions that are expensive to reverse (datastore choice, auth model, framework),
write a short ADR using `.claude/templates/adr-template.md`:

- **Context** — the forces at play.
- **Decision** — what we chose.
- **Consequences** — what we gain and give up.
- **Alternatives** — what we rejected and why.

## Commit & PR text is documentation too

See `02-git-workflow.md`. The diff shows *what*; the message must capture *why*.

## Tone

Be concise, concrete, and honest about limitations. Prefer examples over abstraction.
Don't document aspirational behavior that doesn't exist yet.
