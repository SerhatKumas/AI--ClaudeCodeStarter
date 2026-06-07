# Slash Commands

Project slash commands are prompt macros invoked as `/command-name`. Each is a
Markdown file whose body becomes the prompt. Use `$ARGUMENTS` to capture whatever
the user types after the command.

| Command | Does |
|---------|------|
| `/audit` | Quality + security audit of the current changes |
| `/plan-feature <desc>` | Produce an approvable implementation plan (no code yet) |
| `/ship` | Pre-flight verify + review before opening a PR |
| `/explain <target>` | Explain how some code works, without changing it |

## File format

```markdown
---
description: One-line summary shown in the command list.
---

The prompt Claude runs. Use $ARGUMENTS for user input, and reference
project rules/skills/agents to compose behavior.
```

## Tips

- Commands are great for workflows you trigger often and want to invoke by name.
- Compose them: a command can tell Claude to follow a skill or delegate to an agent.
- Keep the prompt imperative and unambiguous. Subdirectories namespace commands
  (`commands/db/migrate.md` → `/db:migrate`).
