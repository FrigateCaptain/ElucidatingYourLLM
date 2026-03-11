# Markdown Dates — Creation and Last-Updated Dates

**Domain rule.** Apply when working with README.md and overview files.

Globs: `**/*.md`

---

## Markdown Files Date Rule [MANDATORY]

All README.md and overview files must include a creation date and a last-updated date at the bottom.

**Format:**
```markdown
---

*Created: [day] [month] [year], [hours]:[minutes]*
*Last updated: [day] [month] [year], [hours]:[minutes]*
```

**Rules:**
1. **When creating a new file**: both dates are the same — the moment of creation
2. **When updating**: change only "Last updated". Never modify "Created"
3. **Date format**: "5 January 2025, 17:45" (day month year, 24-hour format)

**Scope:** README.md and overview files across all project working directories.
