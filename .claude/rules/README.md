# Rules

These are the project's best-practice references. `CLAUDE.md` links to them so Claude
can pull in depth on demand without bloating every session's context.

| File | Covers |
|------|--------|
| `00-core-principles.md` | The mindset; tie-breaker when rules conflict |
| `01-code-style.md` | Naming, structure, per-language idioms |
| `02-git-workflow.md` | Branching, commits, PRs |
| `03-testing.md` | What/how to test, the pyramid, anti-patterns |
| `04-security.md` | Secrets, injection, authz, the security checklist |
| `05-documentation.md` | Code docs, READMEs, ADRs |
| `06-architecture.md` | Design heuristics, SOLID, performance |
| `07-dependencies.md` | When and how to add third-party code |

**Customize freely.** Delete language sections you don't use, add your team's
conventions, and keep each file focused. If a rule keeps getting violated, that's a
signal to make it sharper — or to encode it as a hook in `settings.json`.
