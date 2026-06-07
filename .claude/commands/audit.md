---
description: Run a quality + security audit of the current changes (or a target) using the project checklists.
---

Run an audit of the changes on the current branch (or of `$ARGUMENTS` if provided —
a path, directory, or "everything").

1. Determine scope. Default to the diff vs. the main branch (`git diff main...HEAD`);
   if `$ARGUMENTS` names a path, audit that instead.
2. Work through the relevant checklists in `.claude/audits/`:
   - `security-checklist.md`
   - `code-quality-checklist.md`
   - `performance-checklist.md` (if perf-sensitive code changed)
3. For broad or security-sensitive scope, delegate to the `security-auditor` and
   `code-reviewer` subagents in parallel and consolidate their findings.
4. Report findings grouped by severity (🔴 must-fix / 🟡 should-fix / 🟢 nit), each
   with `file:line`, the problem, why it matters, and a concrete fix.

Do not change any code unless I explicitly ask — this is a review, not a fix.
