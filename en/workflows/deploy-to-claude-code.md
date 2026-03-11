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
