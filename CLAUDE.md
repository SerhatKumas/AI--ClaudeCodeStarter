# <PROJECT_NAME>

> This file is loaded into Claude's context at the start of every session. Keep it
> concise and high-signal. Put deep references in `.claude/rules/` and link to them.

## What this project is

<One or two sentences: what the product does and who it's for.>

## Tech stack

- **Language(s):** <e.g. TypeScript, Python 3.12>
- **Framework(s):** <e.g. Next.js 15, FastAPI>
- **Database:** <e.g. PostgreSQL via Prisma>
- **Package manager:** <e.g. pnpm / uv / cargo>
- **Testing:** <e.g. Vitest, Playwright, pytest>

## Commands

```bash
<install>      # e.g. pnpm install
<dev>          # e.g. pnpm dev
<test>         # e.g. pnpm test
<lint>         # e.g. pnpm lint
<typecheck>    # e.g. pnpm typecheck
<build>        # e.g. pnpm build
```

> Run `<lint>` and `<typecheck>` before declaring any task done.

## Project layout

```
src/          # <what lives here>
tests/        # <test convention>
...           # <fill in the directories that matter>
```

## Conventions Claude must follow

These are the rules of the house. Detailed guidance lives in `.claude/rules/`:

- **Core principles** — `.claude/rules/00-core-principles.md`
- **Code style** — `.claude/rules/01-code-style.md`
- **Git & commits** — `.claude/rules/02-git-workflow.md`
- **Testing** — `.claude/rules/03-testing.md`
- **Security** — `.claude/rules/04-security.md`
- **Documentation** — `.claude/rules/05-documentation.md`
- **Architecture** — `.claude/rules/06-architecture.md`
- **Dependencies** — `.claude/rules/07-dependencies.md`

## Golden rules (the short version)

1. **Match the surrounding code.** Mirror existing patterns, naming, and structure.
2. **Smallest change that works.** No drive-by refactors unless asked.
3. **Verify before claiming done.** Run tests/lint/typecheck and report real results.
4. **Never invent APIs.** Check the codebase or docs; don't guess function signatures.
5. **Ask when genuinely blocked** on a decision only the user can make — otherwise pick a sane default and note it.
6. **No secrets in code.** Use env vars; never commit credentials.

## Things to avoid

- Don't add dependencies without checking what's already available.
- Don't disable lint rules or tests to make something pass.
- Don't commit, push, or open PRs unless explicitly asked.
- Don't write comments that restate the code; explain *why*, not *what*.

## Domain glossary (optional)

| Term | Meaning |
|------|---------|
| <Term> | <Definition the codebase assumes> |
