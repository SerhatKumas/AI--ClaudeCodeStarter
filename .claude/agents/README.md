# Subagents

Subagents are specialized assistants Claude delegates to. Each runs in its own
context window with its own tools and system prompt, then reports back a result.
They're ideal for focused, parallelizable work (review, audit, search) that you
don't want cluttering the main conversation.

| Agent | Role | Tools |
|-------|------|-------|
| `code-reviewer` | Reviews diffs for correctness, security, clarity | read-only + bash |
| `security-auditor` | Hunts for vulnerabilities against the checklist | read-only + bash |
| `test-writer` | Writes idiomatic tests for existing code | read/write + bash |

## File format

```markdown
---
name: agent-name
description: When Claude should delegate to this agent. Add "use proactively" to encourage automatic use.
tools: Read, Grep, Glob, Bash   # omit to inherit all tools
model: inherit                  # inherit | sonnet | opus | haiku
---

System prompt: the agent's role, process, and output format.
```

## Tips

- **Least privilege:** give reviewers/auditors read-only tools so they can't
  accidentally mutate the repo.
- **Sharp descriptions** drive good delegation — say exactly when to use it.
- **Define the output format** so results come back structured and actionable.
- Keep each agent single-purpose; compose several rather than building one mega-agent.
