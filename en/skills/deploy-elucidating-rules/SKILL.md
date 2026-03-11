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
> - [ ] python-proxy.md — for working with Python through a proxy/VPN: correct proxy forwarding across all HTTP libraries
> - [ ] pre-install-check.md — for installing software via AI: compatibility check against the system before installation (recommended for everyone)
> - [ ] markdown-dates.md — for maintaining documentation in markdown: automatic stamping of creation and update dates
> - [ ] excel-files.md — for working with Excel via Python: standards for reading, writing, and formatting files
> - [ ] generated-docs.md — for generating DOCX/ODT programmatically: structure and formatting standards for generated documents
> - [ ] video-editing.md — for editing video with ffmpeg: ready-made command patterns, error handling
> - [ ] technical-documents.md — for maintaining technical documentation in a `technical/` folder: structure and formatting requirements
> - [ ] file-editing.md — for working with files via AI: literal execution of requests, protection against unsolicited changes, backups (recommended for everyone)
> - [ ] settings-change-tracking.md — for changing settings via AI: automatic recording of all changes in documentation (recommended for everyone)
> - [ ] backlogs-management.md — for managing task backlogs: file structure, registry, workflow
> - [ ] odt-fonts.md — for creating ODT documents: font and formatting standards (LibreOffice)
> - [ ] projects-management.md — for managing projects: registry, backlog, subprojects, naming
> - [ ] rules-management.md — for creating and managing AI assistant rules: placement, structure, registry, validation
> - [ ] skills-management.md — for working with AI assistant skills: security, approval, creation
> - [ ] structural-analogy.md — for creating content modeled on an existing example: preserving structure, links, and dividers"

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
