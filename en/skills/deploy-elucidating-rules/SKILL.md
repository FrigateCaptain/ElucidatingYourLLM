# SKILL: deploy-elucidating-rules

## Purpose

Interactive deployment of rules from the ElucidatingYourLLM repository to Cursor or Claude Code. Asks questions about platform choice, rules, and settings, then creates and places the files.

## When to use

When the user wants to:
- Deploy rules from ElucidatingYourLLM to their Cursor or Claude Code
- Update existing rules to a new version
- Add individual domain rules

## Step-by-step instructions

### Step 1. Determine the platform

Ask the user:
> "Where should we deploy the rules?
> 1. Cursor (`.cursorrules` + `.cursor/rules/`)
> 2. Claude Code (`CLAUDE.md` / `~/.claude/CLAUDE.md`)"

### Step 2. Determine the workspace

**For Cursor:**
> "Which workspace? Provide the path to the project folder, or 'globally' for `~/.cursor/`"

**For Claude Code:**
> "Globally (`~/.claude/CLAUDE.md`) or for a specific project? If for a project — provide the path."

### Step 3. Choose base rules

Show the list and ask:
> "Which base rules to include?
> - [x] core.md (AI behavior, error protection) — recommended
> - [x] information-architecture.md (information architecture) — recommended
> - [x] file-management.md (file management) — recommended
> - [ ] scripts-management.md (scripts management) — needed if you write scripts regularly
> - [x] git-workflow.md (git) — recommended"

### Step 4. Choose domain rules

> "Which domain rules do you need? Select the ones you need:
> - [ ] python-proxy.md — if you use Python + proxy/VPN
> - [ ] pre-install-check.md — recommended for everyone
> - [ ] markdown-dates.md — if you maintain documentation in markdown
> - [ ] excel-files.md — if you work with Excel via Python
> - [ ] generated-docs.md — if you create DOCX/ODT programmatically
> - [ ] video-editing.md — if you work with video via ffmpeg
> - [ ] technical-documents.md — if you maintain a technical/ folder"

### Step 5. Language of rules

> "The rules are written in Russian. Keep them in Russian or adapt to another language?"

### Step 6. Structure for Cursor

**Only for Cursor:** ask about structure:
> "How to organize the rules:
> 1. Monolithic — everything in a single `.cursorrules` (simpler)
> 2. Modular — base rules in `.cursorrules`, domain rules in `.cursor/rules/*.mdc` (recommended)"

### Step 7. Create files

Based on the answers:

1. Check that the `.cursor/rules/` folder exists (for modular Cursor setup)
2. For each selected file from `en/rules/` (or `ru/rules/`): read the content, **remove the lines `*Date created:*` and `*Last updated:*`** (these are service metadata, they must not be included in the user's rules)
3. Create the main rules file (`.cursorrules` or `CLAUDE.md`) from the cleaned content
4. Create domain `.mdc` files with frontmatter (for modular Cursor) from the cleaned content
5. Report to the user: which files were created and where

### Step 8. Verification

Suggest the user verify:
> "Files created. I recommend verifying:
> 1. Start a new conversation in Cursor/Claude Code
> 2. Ask: \"What rules do you have?\"
> 3. The AI should reproduce the key principles"

### Step 9. Personalization

Suggest the next step:
> "Rules are deployed. Would you like to personalize them now — remove unnecessary sections, change the language policy, or add project-specific rules?"

## Notes

- When updating to a new version: first show CHANGELOG.md, then ask which changes to apply
- If rules already exist — warn the user and create a backup (suffix `.backup`)
- The path to the ElucidatingYourLLM repository should be confirmed with the user or determined automatically (current folder if the repository is open)
