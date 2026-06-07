# Claude Code Starter

> A fork-and-go scaffold for building software with [Claude Code](https://claude.com/claude-code) —
> the "Spring Initializr" for vibe coding.

## What is this?

When you open [Claude Code](https://claude.com/claude-code) in a repo, it works best
when it knows **your project's conventions, your workflows, and your guardrails**.
Without that, every session starts from zero — you re-explain how to test, what style
to follow, and what not to touch.

**Claude Code Starter** is a ready-made `.claude/` directory (plus matching GitHub
config) that encodes software engineering best practices so Claude — and your whole
team — works consistently from day one. Drop it into any repository and you
immediately get:

- 📜 **Rules** — best-practice references for style, testing, security, git, and architecture
- ⚡ **Skills** — repeatable workflows you trigger by name (`/implement-feature`, `/fix-bug`)
- 🤖 **Subagents** — specialists for code review, security audits, and test writing
- 🎛️ **Slash commands** — quick macros like `/audit`, `/plan-feature`, `/ship`
- ✅ **Audit checklists** — for security, code quality, performance, accessibility, releases
- 🧰 **Templates** — PR, ADR, and issue scaffolds
- 🔧 **Settings** — least-privilege permissions so Claude stops asking about safe commands
- 🚦 **CI** — language-agnostic GitHub Actions that work the moment you fork

It's **language- and framework-agnostic** on purpose. The defaults apply to almost
any project; you fill in your stack-specific bits where marked.

## Why use it?

| Without a `.claude/` setup | With this starter |
|----------------------------|-------------------|
| Re-explain conventions every session | Conventions live in version control |
| Inconsistent code across teammates/agents | One shared source of truth |
| Claude asks permission for routine commands | Safe commands pre-approved |
| Ad-hoc reviews that miss things | Checklists + specialist agents |
| Quality depends on who's prompting | Quality baked into the workflow |

## Repository layout

```
your-project/
├── CLAUDE.md                  # Project memory — loaded into Claude every session
├── .claude/
│   ├── settings.json          # Shared permissions, env, hooks (committed)
│   ├── settings.local.json    # Personal, machine-specific overrides (git-ignored)
│   ├── rules/                 # Best-practice references Claude consults on demand
│   ├── skills/                # Reusable multi-step workflows (/skill-name)
│   ├── agents/                # Specialized subagents Claude delegates to
│   ├── commands/              # Project slash commands (/audit, /ship, …)
│   ├── audits/                # Review checklists (security, quality, perf, a11y)
│   └── templates/             # PR / ADR / issue scaffolds
└── .github/
    ├── workflows/             # Language-agnostic CI (hygiene, secrets, deps, stale)
    ├── dependabot.yml         # Dependency update config
    ├── PULL_REQUEST_TEMPLATE.md
    └── ISSUE_TEMPLATE/        # Bug + feature templates
```

## What each piece is for

### `CLAUDE.md` — the single most important file
This is the project's **memory**. Claude Code loads it automatically at the start of
every session, so it's where your stack, run commands, directory layout, and golden
rules live. Keep it **short and high-signal** — it costs context on every turn — and
link out to `rules/` for the deep stuff.

### `.claude/rules/` — the "why" behind your standards
Detailed best-practice documents Claude reads **on demand** (linked from `CLAUDE.md`)
so they don't bloat every session. They explain the reasoning, so Claude applies
judgment instead of blindly following orders.

| File | Covers |
|------|--------|
| `00-core-principles.md` | The mindset; the tie-breaker when rules conflict |
| `01-code-style.md` | Naming, structure, and per-language idioms |
| `02-git-workflow.md` | Branching, Conventional Commits, PRs |
| `03-testing.md` | What/how to test, the test pyramid, anti-patterns |
| `04-security.md` | Secrets, injection, authz, the security checklist |
| `05-documentation.md` | Code docs, READMEs, ADRs |
| `06-architecture.md` | Design heuristics, SOLID, performance |
| `07-dependencies.md` | When and how to add third-party code |

### `.claude/skills/` — workflows you trigger by name
Skills are reusable, multi-step procedures. Type `/implement-feature` and Claude
follows a disciplined plan→build→test→verify flow instead of winging it.

| Skill | Use when |
|-------|----------|
| `/implement-feature` | Building a new feature end-to-end |
| `/fix-bug` | Diagnosing and fixing something broken (reproduce → root cause → regression test) |
| `/refactor-safely` | Restructuring code without changing behavior, guarded by tests |

### `.claude/agents/` — specialists Claude delegates to
Subagents run in their own context with their own tools and report back. They keep
focused work (reviews, audits) out of your main conversation and can run in parallel.

| Agent | Role |
|-------|------|
| `code-reviewer` | Reviews diffs for correctness, security, and clarity (read-only) |
| `security-auditor` | Hunts for vulnerabilities against the security checklist (read-only) |
| `test-writer` | Writes idiomatic tests matching your project's conventions |

### `.claude/commands/` — quick prompt macros
Slash commands are short, named prompts. They compose the rest of the kit — a command
can tell Claude to follow a skill or delegate to an agent.

| Command | Does |
|---------|------|
| `/audit` | Quality + security audit of the current changes |
| `/plan-feature <desc>` | Produces an approvable implementation plan (no code yet) |
| `/ship` | Pre-flight verify + review before opening a PR |
| `/explain <target>` | Explains how some code works, without changing it |

### `.claude/audits/` — checklists for reviews & releases
Literal checklists the `/audit` command and agents work through. Mark each item ✅ / ⚠️ / ❌
with a `file:line` and a note.

`security-checklist` · `code-quality-checklist` · `performance-checklist` ·
`accessibility-checklist` · `pre-release-checklist`

### `.claude/templates/` — consistent documents
Scaffolds for `pr-description`, `adr` (architecture decision records), and `issue`,
so generated docs always follow the same shape.

### `.claude/settings.json` — permissions, env & hooks
Controls what Claude can do without asking. Uses an **allow / ask / deny** model:
safe read-only commands flow freely, risky ones (force-push, `rm -rf`, reading `.env`)
are blocked. Committed to git so the whole team shares it. Personal tweaks go in
`settings.local.json` (git-ignored).

### `.github/` — CI and collaboration
Language-agnostic GitHub Actions that work on any repo (see [Continuous integration](#continuous-integration)),
plus PR/issue templates that mirror the `.claude/templates/` formats.

## Getting started

### Option A — Start a brand-new project from this template
1. Click **“Use this template”** on GitHub (or `git clone` and delete `.git`).
2. Follow [Configure it for your project](#configure-it-for-your-project) below.

### Option B — Add it to an existing project
Copy the scaffold into your repo's root:

```bash
# from the parent dir of both folders
cp -r claude-code-starter/.claude    your-project/.claude
cp -r claude-code-starter/.github    your-project/.github    # skip if you already have one
cp    claude-code-starter/CLAUDE.md  your-project/CLAUDE.md
cp    claude-code-starter/.gitignore your-project/.gitignore  # or merge the .claude entries
```

> Already have a `.github/` or `.gitignore`? **Merge** rather than overwrite — copy in
> only the files/lines you want (e.g. add `.claude/settings.local.json` to your ignore file).

### Configure it for your project
1. **Edit [CLAUDE.md](CLAUDE.md).** Replace every `<PLACEHOLDER>` — project name, tech
   stack, install/dev/test/lint/build commands, and directory layout. This is the
   highest-leverage step.
2. **Trim [rules/01-code-style.md](.claude/rules/01-code-style.md).** Delete the
   language sections you don't use; add your team's conventions.
3. **Tune [.claude/settings.json](.claude/settings.json).** Add the commands your team
   runs often to the `allow` list (e.g. your test runner) so Claude stops asking.
   Copy `settings.local.json.example` → `settings.local.json` for personal overrides.
4. **Enable CI.** Open `.github/workflows/ci.yml`, uncomment the `project-checks` job,
   and fill in your real install/lint/test/build commands. Uncomment your ecosystem in
   `.github/dependabot.yml`.
5. **Commit it.** Everything except `settings.local.json` is meant to be shared.

### Try it out
Open Claude Code in your repo and run any of these:

```text
/plan-feature add CSV export to the reports page
/audit
/explain how authentication works in this codebase
```

You can also just chat normally — Claude now has your `CLAUDE.md` and rules loaded,
and will pull in skills, agents, and commands as they become relevant.

## Continuous integration

The included GitHub Actions are **deliberately language-agnostic** — they only run
checks that apply to almost any repo, so they work the moment you fork:

- **Repo hygiene** — blocks merge-conflict markers and oversized files; warns on
  stray `TODO`/`FIXME`/`debugger`.
- **Conventional commits** — validates PR commit messages against the format in
  `rules/02-git-workflow.md`.
- **Secret scanning** — [gitleaks](https://github.com/gitleaks/gitleaks) on every push/PR.
- **Dependency review** — flags vulnerable or badly-licensed deps added in a PR.
- **Stale triage** + **Dependabot** for GitHub Actions.

Build/lint/test/typecheck are **yours to add** — `.github/workflows/ci.yml` has a
commented `project-checks` job with `TODO` slots. Uncomment it, add your runtime
setup, and drop in your real commands. Nothing language-specific is assumed.

## Design principles

- **Keep `CLAUDE.md` short.** It loads every turn — link out to `rules/` for depth.
- **Rules are reference, not rote.** They explain *why*, so Claude applies judgment.
- **Skills/commands encode workflows you repeat.** If you've explained it twice, codify it.
- **Least privilege in settings.** Allow safe read-only commands; confirm the risky ones.
- **Everything is editable.** This is a starting point — delete what you don't need.

## FAQ

**Do I need all of it?** No. Delete anything you won't use — it's a starting point,
not a contract. The only near-essential file is `CLAUDE.md`.

**Will this work for my language?** Yes. The defaults are language-agnostic; the only
stack-specific spots are clearly marked (`<PLACEHOLDER>` in `CLAUDE.md`, the language
sections in `rules/01-code-style.md`, and the commented CI/Dependabot blocks).

**Do my teammates need to do anything?** They just need Claude Code. Once the `.claude/`
folder is committed, everyone gets the same rules, skills, and commands automatically.

**Is `settings.local.json` shared?** No — it's git-ignored for personal, machine-specific
overrides. The shared config is `settings.json`.

**How do I add my own skill/command/agent?** Each folder has a `README.md` documenting
its file format. Copy an existing example and adapt it.

**Does this only work in the terminal?** No. Claude Code reads `.claude/` the same way
across the CLI, the desktop and web apps, and the IDE extensions.

## Contributing & license

- **Contributing:** see [CONTRIBUTING.md](CONTRIBUTING.md) for how to propose rules,
  skills, agents, or commands, plus the file formats and PR workflow.
- **Code of Conduct:** participation is governed by [CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md).
- **License:** [MIT](LICENSE) — free to use, fork, modify, and ship in your own
  projects, commercial or otherwise.

---

Made to be forked. Contributions, issues, and stars welcome. 🌟
