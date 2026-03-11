# Deploy to Claude Code

Step-by-step guide for deploying rules from this repository into Claude Code (Anthropic).

---

## Differences from Cursor

| Parameter | Cursor | Claude Code |
|-----------|--------|-------------|
| Main file | `.cursorrules` | `CLAUDE.md` |
| Domain rules | `.cursor/rules/*.mdc` with globs | `.claude/rules/` (folder hierarchy) |
| Glob-based activation | yes | no — everything is managed via file placement |
| alwaysApply | yes | no |

Claude Code has no automatic rule loading based on file type. Context management is handled through a `CLAUDE.md` hierarchy: global (`~/.claude/CLAUDE.md`), project root (`CLAUDE.md`), and subfolders.

---

## Step 1. Answer the setup questions

### 1.1 Scope of application

**Question:** Where do you want to apply the rules?
- **Globally** (across all projects) → files in `~/.claude/`
- **For a specific project** → files in the project root
- **For a subfolder** → files in the subfolder

### 1.2 Domain rules

Browse `en/rules/domain/`. In Claude Code, domain rules aren't loaded automatically — you need to either include them directly in the main `CLAUDE.md` or place them in `.claude/rules/` and reference them manually.

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

**Question:** Do you want to embed domain rules directly into `CLAUDE.md` (simpler) or organize them in `.claude/rules/` (cleaner when you have many rules)?

---

## Step 2. Create CLAUDE.md

**For global application:**
```bash
mkdir -p ~/.claude
```
Create `~/.claude/CLAUDE.md`

**For a project:**
Create `CLAUDE.md` in the project root.

---

## Step 3. Populate CLAUDE.md

Use the skill `deploy-elucidating-rules` (file `en/skills/deploy-elucidating-rules/SKILL.md`) — it automatically creates files and strips service lines (creation and update dates) from the content.

If deploying manually: copy the contents of the relevant files from `en/rules/` into `CLAUDE.md` and **remove the lines `*Date created:*` and `*Last updated:*`** — these are service metadata and must not end up in your rules.

---

## Step 4. Verify everything works

```bash
claude   # launch in the project folder
# then ask: "What rules do you have?"
```

---

## Updating

When a new version is released:
1. `git pull` in the ElucidatingYourLLM folder
2. Check CHANGELOG.md
3. Apply the relevant changes to `CLAUDE.md`
