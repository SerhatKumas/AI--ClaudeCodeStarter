# Audits

Reusable checklists for reviewing changes before they ship. The `/audit` command and
the `code-reviewer` / `security-auditor` agents reference these. Use them as
literal checklists — mark each item ✅ / ⚠️ / ❌ with a `file:line` and note.

| Checklist | When to run |
|-----------|-------------|
| `security-checklist.md` | Any security-sensitive change; before release |
| `code-quality-checklist.md` | Every meaningful change / PR |
| `performance-checklist.md` | Hot paths, data access, large collections, UI rendering |
| `accessibility-checklist.md` | User-facing web/UI changes |
| `pre-release-checklist.md` | Before tagging a release or deploying to prod |

Tailor these to your domain — add items the hard way (after an incident) so they're
never forgotten the easy way.
