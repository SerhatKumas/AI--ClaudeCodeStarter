---
description: Pre-flight check before opening a PR — verify, audit, and prepare the change.
---

Run pre-flight checks on the current change before it ships. Target: `$ARGUMENTS`
(defaults to the current branch's diff vs. main).

1. **Verify** — run the project's test, lint, and typecheck commands (see
   `CLAUDE.md`). Report actual results. Stop and surface anything red.
2. **Self-review** — run the `code-reviewer` subagent on the diff; summarize
   must-fix items.
3. **Security pass** — run the `security-auditor` subagent if the change touches
   auth, input handling, data, or dependencies.
4. **Docs check** — confirm README/docs/env examples were updated if behavior or
   setup changed (`rules/05-documentation.md`).
5. **Summarize readiness** — a checklist of what passed/failed and any blockers.
6. If everything is green and I confirm, draft a PR description using
   `.claude/templates/pr-description.md`. Do **not** commit, push, or open the PR
   until I explicitly say so.
