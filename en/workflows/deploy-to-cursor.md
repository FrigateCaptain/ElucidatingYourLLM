# Deploy to Cursor

Step-by-step guide for deploying rules from this repository into Cursor.

---

## Step 1. Answer the setup questions

### 1.1 Core rules

Core rules (`en/rules/core.md`, `en/rules/information-architecture.md`, `en/rules/file-management.md`, `en/rules/scripts-management.md`, `en/rules/git-workflow.md`) — it's recommended to include all of them.

**Question:** Do you want the full "Scripts Management" section? It enforces a mandatory cycle: spec file → header → registry every time a script is created. If you don't write scripts regularly, you can stick with a simplified version.

### 1.2 Domain rules

Browse the `en/rules/domain/` folder. For each file, decide whether to include it or not.

| File | When you need it |
|------|------------------|
| `python-proxy.md` | You use Python with a proxy/VPN |
| `pre-install-check.md` | You install software via AI (recommended for everyone) |
| `markdown-dates.md` | You maintain documentation in markdown |
| `excel-files.md` | You work with Excel via Python |
| `generated-docs.md` | You generate DOCX/ODT files programmatically |
| `video-editing.md` | You edit video with ffmpeg |
| `technical-documents.md` | You maintain technical docs in a `technical/` folder |

### 1.3 Rules language

The rules are written in Russian. If you need them in another language, adapt the file contents accordingly.

### 1.4 Rules storage structure

Two options for organizing rules in Cursor:

**Option A — monolithic** (everything in one file):
- All content → a single `.cursorrules` file in the workspace root
- Simpler, but rules are loaded into every conversation

**Option B — modular** (recommended):
- Core rules → `.cursorrules`
- Domain rules → `.cursor/rules/*.mdc` with matching globs
- Rules are loaded only when you're working with relevant files

---

## Step 2. Create the folder structure

```bash
mkdir -p .cursor/rules
```

---

## Step 3. Place the core rules

Use the skill `deploy-elucidating-rules` (file `en/skills/deploy-elucidating-rules/SKILL.md`) — it automatically asks setup questions, creates the needed files, and strips service lines (creation and update dates) from the content.

If deploying manually: create `.cursorrules` in the workspace root, copy the contents of the relevant files from `en/rules/` into it, and **remove the lines `*Date created:*` and `*Last updated:*`** — these are service metadata and must not end up in your rules.

---

## Step 4. Place the domain rules

For each file you selected from `en/rules/domain/`, create a corresponding `.mdc` in `.cursor/rules/`:

```
en/rules/domain/python-proxy.md        → .cursor/rules/python-proxy.mdc
en/rules/domain/pre-install-check.md   → .cursor/rules/pre-install-check.mdc
en/rules/domain/markdown-dates.md      → .cursor/rules/markdown-dates.mdc
...
```

Add YAML frontmatter to the beginning of each `.mdc`:

```yaml
---
description: "Brief description of the rule"
globs: "**/*.py"       # file pattern (see the table below)
alwaysApply: false
---
```

Recommended globs:

| Rule | globs | alwaysApply |
|------|-------|-------------|
| python-proxy | `**/*.py` | false |
| pre-install-check | — | true |
| markdown-dates | `**/*.md` | false |
| excel-files | `**/*.xlsx, **/*.xls` | false |
| generated-docs | `**/*.docx, **/*.odt` | false |
| video-editing | `**/*.mp4, **/*.mkv, **/*.avi, **/*.webm, **/*.mov` | false |
| technical-documents | `**/technical/**/*.md` | false |

---

## Step 5. Verify everything works

1. Open Cursor in the workspace folder
2. Start a new conversation
3. Ask: "What rules do you have?" or "Read .cursorrules"
4. Make sure the AI sees the rules

For domain rules: open a file with the matching extension (e.g. `.py`) and verify the AI references the rules from the `.mdc`.

---

## Step 6. Personalization

Once verified, adapt the rules for your needs:
- Change the language policy
- Add or remove sections
- Add rules specific to your project

---

## Updating

When a new version of the rules is released:
1. `git pull` in the ElucidatingYourLLM folder
2. Check CHANGELOG.md for what changed
3. Apply the relevant changes to your `.cursorrules` and `.mdc` files
