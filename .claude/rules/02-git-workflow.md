# Git & Commit Workflow

> Claude must NOT commit, push, or open PRs unless explicitly asked. When asked,
> follow this.

## Branching

- Never commit directly to `main`/`master`. Branch first.
- Name branches `<type>/<short-description>`: `feat/oauth-login`,
  `fix/null-cart-total`, `chore/bump-deps`.

## Commit messages (Conventional Commits)

```
<type>(<optional scope>): <imperative summary, ≤72 chars>

<body: what changed and WHY. Wrap at ~72 cols. Omit if the summary says it all.>

<footer: BREAKING CHANGE: …, Closes #123, etc.>
```

**Types:** `feat`, `fix`, `docs`, `style`, `refactor`, `perf`, `test`, `build`,
`ci`, `chore`, `revert`.

**Good:**
```
fix(cart): prevent negative totals when a coupon exceeds subtotal

Coupons were applied without clamping, so a $10 coupon on a $4 cart
produced -$6. Clamp the discount to the subtotal before tax.

Closes #482
```

**Bad:** `update`, `fix stuff`, `wip`, `asdf`.

## Commit hygiene

- One logical change per commit. Don't mix a refactor with a feature.
- Don't commit generated files, secrets, or commented-out code.
- Run lint/tests before committing; don't commit a red build.
- Review your own diff (`git diff --staged`) before every commit.

## Pull requests

- Keep PRs small and reviewable (aim < ~400 lines of meaningful diff).
- Use the template in `.claude/templates/pr-description.md`.
- Describe **what**, **why**, **how to test**, and **risk/rollback**.
- Link the issue. Call out anything reviewers should scrutinize.

## What Claude appends to commits/PRs

When the user asks Claude to commit, end the commit message with the required
co-author trailer, and end PR bodies with the Claude Code attribution line, per the
harness instructions. Never fabricate co-authors or issue numbers.

## Never

- `git push --force` to a shared branch (use `--force-with-lease` if you must).
- `git reset --hard` / `git clean -fd` without explicit confirmation.
- Rewriting published history that teammates have pulled.
