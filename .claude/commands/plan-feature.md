---
description: Produce an implementation plan for a feature before any code is written.
---

Create an implementation plan for: **$ARGUMENTS**

Do NOT write code yet. Investigate and produce a plan I can approve.

1. **Clarify** — restate the goal and list any ambiguities or decisions only I can
   make. Ask up to 3 sharp questions if needed.
2. **Explore** — find the closest existing patterns in the codebase and the files
   that will be touched. Cite them as `file:line`.
3. **Plan** — present:
   - the approach in a few sentences,
   - an ordered list of concrete edits (file by file),
   - the test strategy,
   - risks, trade-offs, and anything hard to reverse (schema/API/dep changes),
   - alternatives considered and why you'd reject them.
4. Keep it tight and concrete. End by asking me to approve or adjust before you
   implement.

Follow `.claude/skills/implement-feature/SKILL.md` once I approve.
