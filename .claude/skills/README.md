# Skills

Skills are reusable, multi-step workflows Claude can invoke. Each lives in its own
folder as `SKILL.md` with YAML frontmatter (`name`, `description`). The description
is how Claude decides when a skill is relevant, so make it specific.

| Skill | Use when |
|-------|----------|
| `implement-feature` | Building a new feature/capability end-to-end |
| `fix-bug` | Diagnosing and fixing something broken |
| `refactor-safely` | Restructuring code without changing behavior |

## Writing your own

```markdown
---
name: my-skill
description: One sentence on WHAT it does and WHEN to use it. Be specific — this is the trigger.
---

# My Skill

Step-by-step instructions Claude follows when the skill runs. Reference the
project's rules (e.g. `rules/03-testing.md`) instead of repeating them.
```

Tips:
- Skills can bundle supporting files in the same folder (scripts, templates).
- Keep instructions imperative and ordered.
- A great `description` is the difference between a skill that fires at the right
  time and one that never does.
