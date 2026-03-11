# Deploy to OpenClaw

Step-by-step guide for integrating rules into an OpenClaw agent workspace.

---

## OpenClaw workspace architecture

OpenClaw populates the agent's workspace with a set of `.md` files. The agent reads them at the start of every session.

Key workspace files:
```
~/.openclaw/workspace/
├── AGENTS.md      ← main instructions (workflow, protocols)
├── SOUL.md        ← agent principles and character
├── IDENTITY.md    ← name, style, emoji
├── USER.md        ← user profile
├── TOOLS.md       ← local tool settings
└── memory/
    └── YYYY-MM-DD.md
```

---

## Step 1. Answer the questions

### 1.1 What to adapt

**Question:** What do you want to bring into OpenClaw?
- Behavior rules only (core) → go into `AGENTS.md` / `SOUL.md`
- Script management rules → go into `AGENTS.md` (scripts section)
- Domain rules → only if the agent performs relevant tasks

Full list of domain rules with a description of what each one provides:

| File | What it provides | Applicability on VPS |
|------|-----------------|----------------------|
| `python-proxy.md` | For working with Python through a proxy/VPN: correct proxy forwarding across all HTTP libraries | Applicable |
| `pre-install-check.md` | For installing software via AI: compatibility check against the system before installation | Applicable |
| `markdown-dates.md` | For maintaining documentation in markdown: automatic stamping of creation and update dates | Applicable |
| `excel-files.md` | For working with Excel via Python: standards for reading, writing, and formatting files | Applicable |
| `generated-docs.md` | For generating DOCX/ODT programmatically: structure and formatting standards for generated documents | Applicable |
| `video-editing.md` | For editing video with ffmpeg: ready-made command patterns, error handling | Applicable |
| `technical-documents.md` | For maintaining technical documentation in a `technical/` folder: structure and formatting requirements | Applicable |
| `file-editing.md` | For working with files via AI: literal execution of requests, protection against unsolicited changes, backups | Applicable (recommended for everyone) |
| `settings-change-tracking.md` | For changing settings via AI: automatic recording of all changes in documentation | Applicable (recommended for everyone) |
| `backlogs-management.md` | For managing task backlogs: file structure, registry, workflow | Applicable |
| `odt-fonts.md` | For creating ODT documents: font and formatting standards (LibreOffice) | Applicable |
| `projects-management.md` | For managing projects: registry, backlog, subprojects, naming | Applicable |
| `rules-management.md` | For creating and managing AI assistant rules: placement, structure, registry, validation | **Requires adaptation** (see Step 3a) |
| `skills-management.md` | For working with AI assistant skills: security, approval, creation | **Requires adaptation** (see Step 3a) |
| `structural-analogy.md` | For creating content modeled on an existing example: preserving structure, links, and dividers | Applicable |

### 1.2 VPS agent specifics

Some rules don't apply to a VPS-based agent:
- GUI tool rules — not applicable
- Rules referencing local laptop paths — need adaptation
- SSH rules — apply in reverse (the agent itself is the remote server)

---

## Step 2. Map rules to workspace files

| Rule | Where it goes in OpenClaw |
|------|--------------------------|
| AI behavior, self-assessment, role | `SOUL.md` |
| Error prevention, verification | `AGENTS.md` (Safety section) |
| Response format, communication | `SOUL.md` |
| Scripts Management | `AGENTS.md` (Scripts section) |
| Git Workflow | `AGENTS.md` (Git section) |
| Information Architecture | `AGENTS.md` (Memory/Knowledge section) |
| Domain rules (all selected in Step 1.1) | `AGENTS.md` (corresponding section) |

---

## Step 3. Adapt for the sandbox model

OpenClaw uses sandbox isolation: each session gets a copy of the workspace.

When adapting rules:
- Paths: replace absolute laptop paths with VPS paths
- Tools: remove GUI-specific rules
- Memory: add rules for using `memory/YYYY-MM-DD.md`

---

## Step 3a. Adapting platform-specific rules

If `rules-management` and/or `skills-management` were selected in Step 1.1 — these rules contain Cursor-specific terms (`.mdc`, `globs`, `.cursor/rules/`). When deploying to OpenClaw, apply the following adaptation:

### Concept mapping table

| Concept in the rule | In Cursor | In OpenClaw |
|---------------------|-----------|-------------|
| Main rules file | `.cursorrules` | `AGENTS.md` / `SOUL.md` |
| Domain rules | `.cursor/rules/*.mdc` with globs | Sections in `AGENTS.md` or separate `.md` files in workspace |
| Rule metadata | YAML frontmatter (`description`, `globs`, `alwaysApply`) | Section heading |
| File-type-based activation | `globs` | None (everything loads at all times) |
| Rules registry | `RULES_REGISTRY.md` | Table of contents of workspace files |
| Skills | `.cursor/skills/<name>/SKILL.md` | Instructions and procedures in `AGENTS.md` or `TOOLS.md` |
| Skills security | Local only, explicit approval required | Explicit approval required |

### How to adapt `rules-management`

1. Read `en/rules/domain/rules-management.md`
2. Replace terms using the table above
3. Remove the "Activation type" section (no globs/alwaysApply in OpenClaw)
4. Keep unchanged: one rule = one goal, no duplication, size control, registry, validation
5. Result — a "Rules Management" section in `AGENTS.md`

### How to adapt `skills-management`

1. Read `en/rules/domain/skills-management.md`
2. Replace "`.cursor/skills/<name>/SKILL.md`" → "instructions in `AGENTS.md` or `TOOLS.md`"
3. Remove "Global skills `~/.cursor/skills/`" (no equivalent)
4. Keep unchanged: local only, explicit approval required, no external sources
5. Result — a "Skills Management" section in `AGENTS.md`

---

## Step 4. Edit SOUL.md

> **Note**: when copying content from `en/rules/` files — **remove the lines `*Date created:*` and `*Last updated:*`** at the end of each file. These are service metadata and must not end up in the agent workspace.

Example block to add to `SOUL.md`:

```markdown
## Behavior principles

[copy contents of en/rules/core.md, sections "AI Assistant Behavior", "Self-Reflection"]

## Error prevention

[copy contents of en/rules/core.md, section "Technical Claims Verification"]
```

---

## Step 5. Edit AGENTS.md

Add a section with working rules to `AGENTS.md`. Example structure:

```markdown
## Rules

### Behavior
[from SOUL.md — brief references]

### Scripts
[from en/rules/scripts-management.md — adapted version]

### Git
[from en/rules/git-workflow.md]
```

---

## Verification

After editing:
1. Launch the agent: `openclaw agent`
2. Ask: "What are your rules for working with scripts?"
3. Make sure the agent reproduces the key principles

---

## Updating

When a new version of the rules is released:
1. `git pull` in the ElucidatingYourLLM folder
2. Check CHANGELOG.md
3. Manually apply the changes to `SOUL.md` and `AGENTS.md` on the VPS
