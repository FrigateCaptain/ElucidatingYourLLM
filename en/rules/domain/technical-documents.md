# Technical Documents — Formatting Documents in technical/

**Domain rule.** Apply when creating/editing .md files in `technical/`.

Globs: `**/technical/**/*.md`

---

## Document Purpose

Every document in `technical/` must include a **"Document purpose"** field at the top (after the title) — one or two sentences explaining why it exists and who benefits from it.

## Document Structure

### Title
- First level: `# Document Title`
- Clear, descriptive name

### Table of Contents (required element)
Immediately after the title:
```markdown
## Contents

- [Section Name 1](#anchor-link)
- [Section Name 2](#anchor-link-2)
```
Anchors: all lowercase, spaces → hyphens, special characters removed. Follow the table of contents with `---`.

### Sections
- `##` — main sections
- `###` — subsections

## Formatting
- **Bold** for terms, *italics* for emphasis
- Code blocks with language specified
- External links: `[text](URL)`, internal links: `[name](../technical/file.md)`

## File Naming
- Descriptive names, underscores instead of spaces
- Technical terms: `about_markdown_language.md`

## Dates (required element)
At the end of the document:
```markdown
---

**Created:** YYYY-MM-DD
**Last updated:** YYYY-MM-DD
```

## Pre-Save Checklist
- "Document purpose" is present
- Table of contents with working anchors is present
- Creation and update dates are included
- Section structure is logical
