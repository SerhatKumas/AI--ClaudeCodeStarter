# Contributing

Thanks for helping improve **Claude Code Starter**! This project was created and is
maintained by **Serhat Kumas**. It's a scaffold meant to be forked, so contributions
that make the defaults more useful, more correct, or more broadly applicable are
especially welcome.

By participating, you agree to abide by the [Code of Conduct](CODE_OF_CONDUCT.md).

## Ways to contribute

- **Improve the rules** — sharpen guidance in `.claude/rules/`, fix something
  misleading, or add a widely-applicable best practice.
- **Add or refine skills/commands/agents** — new reusable workflows that most projects
  would benefit from.
- **Extend the audit checklists** — items that are easy to forget and costly to miss.
- **Fix the CI / templates** — keep `.github/` working and language-agnostic.
- **Docs** — clarify the README or any folder's `README.md`.

## Guiding principle: stay language-agnostic

The core value of this starter is that it works for **any** project. Keep
contributions framework- and language-neutral. If something is stack-specific, put it
behind a clearly marked placeholder, a commented block, or an optional section — never
hard-code one ecosystem into the defaults.

## Project conventions

This repo eats its own dog food — follow the rules it ships with:

- **Commits:** [Conventional Commits](.claude/rules/02-git-workflow.md), e.g.
  `docs(rules): clarify the testing pyramid`. CI validates this on PRs.
- **Style & principles:** see [`.claude/rules/`](.claude/rules/).
- **No secrets**, no oversized files (CI blocks >5 MB), no merge-conflict markers.

### File formats

When adding to the kit, match the documented format — each folder has a `README.md`:

| Adding a… | Goes in | Format |
|-----------|---------|--------|
| Rule | `.claude/rules/NN-name.md` | Markdown; explain the *why* |
| Skill | `.claude/skills/<name>/SKILL.md` | YAML frontmatter (`name`, `description`) + steps |
| Subagent | `.claude/agents/<name>.md` | Frontmatter (`name`, `description`, `tools`, `model`) + system prompt |
| Command | `.claude/commands/<name>.md` | Frontmatter (`description`) + prompt using `$ARGUMENTS` |
| Checklist | `.claude/audits/<name>-checklist.md` | Markdown checkbox list |
| Template | `.claude/templates/<name>.md` | The scaffold itself |

After adding a file, update the relevant folder `README.md` and the table in the root
[README.md](README.md) so it's discoverable.

## Development workflow

1. **Fork** the repo and create a branch: `git checkout -b feat/your-change`.
2. **Make your change**, keeping it focused — one logical change per PR.
3. **Validate locally:**
   - YAML parses (workflows, dependabot): `ruby -ryaml -e "YAML.load_file(ARGV[0])" <file>`
     (or any YAML linter).
   - Markdown links resolve and tables render.
   - No secrets, no files >5 MB, no leftover `TODO`/`FIXME`.
4. **Open a PR** using the [pull request template](.github/PULL_REQUEST_TEMPLATE.md).
   Describe *what* changed and *why*, and how a reviewer can check it.
5. CI (hygiene, conventional-commits, secret scan, dependency review) must pass.

## Reporting issues

Use the [issue templates](.github/ISSUE_TEMPLATE/) — bug reports with a clear
reproduction and feature requests with a concrete "what done looks like" get acted on
fastest.

## Questions

Open a discussion or a question-type issue. The maintainer, Serhat Kumas, is happy to
help you adapt the starter to your team.

---

Every contribution, big or small, makes the starter better for the next person who
forks it. Thank you! 🙌
