# Deploy to Cursor

Step-by-step guide for deploying rules from this repository into Cursor.

---

## Step 1. Answer the setup questions

### 1.1 Core rules

Core rules (`en/rules/core.md`, `en/rules/information-architecture.md`, `en/rules/file-management.md`, `en/rules/scripts-management.md`, `en/rules/git-workflow.md`) — it's recommended to include all of them.

**Question:** Do you want the full "Scripts Management" section? It enforces a mandatory cycle: spec file → header → registry every time a script is created. If you don't write scripts regularly, you can stick with a simplified version.

### 1.2 Domain rules

Browse the `en/rules/domain/` folder. For each file, decide whether to include it or not.

| File | What it provides |
|------|-----------------|
| `python-proxy.md` | For working with Python through a proxy/VPN: correct proxy forwarding across all HTTP libraries |
| `pre-install-check.md` | For installing software via AI: compatibility check against the system before installation (recommended for everyone) |
| `markdown-dates.md` | For maintaining documentation in markdown: automatic stamping of creation and update dates |
| `excel-files.md` | For working with Excel via Python: standards for reading, writing, and formatting files |
| `generated-docs.md` | For generating DOCX/ODT programmatically: structure and formatting standards for generated documents |
| `video-editing.md` | For editing video with ffmpeg: ready-made command patterns, error handling |
| `technical-documents.md` | For maintaining technical documentation in a `technical/` folder: structure and formatting requirements |
| `file-editing.md` | For working with files via AI: literal execution of requests, protection against unsolicited changes, backups (recommended for everyone) |
| `settings-change-tracking.md` | For changing settings via AI: automatic recording of all changes in documentation (recommended for everyone) |
| `backlogs-management.md` | For managing task backlogs: file structure, registry, workflow |
| `odt-fonts.md` | For creating ODT documents: font and formatting standards (LibreOffice) |
| `projects-management.md` | For managing projects: registry, backlog, subprojects, naming |
| `rules-management.md` | For creating and managing AI assistant rules: placement, structure, registry, validation |
| `skills-management.md` | For working with AI assistant skills: security, approval, creation |
| `structural-analogy.md` | For creating content modeled on an existing example: preserving structure, links, and dividers |

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
| file-editing | — | true |
| settings-change-tracking | — | true |
| backlogs-management | `**/backlogs/**` | false |
| odt-fonts | `**/*.odt` | false |
| projects-management | — (description-based) | false |
| rules-management | `.cursor/rules/**` | false |
| skills-management | `.cursor/skills/**` | false |
| structural-analogy | `**/*.md` | false |

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
