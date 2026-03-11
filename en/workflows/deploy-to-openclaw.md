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
- Domain rules → only if the agent performs relevant tasks (Python, ffmpeg, etc.)

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
| Domain rules (Python, ffmpeg) | `AGENTS.md` (corresponding section) |

---

## Step 3. Adapt for the sandbox model

OpenClaw uses sandbox isolation: each session gets a copy of the workspace.

When adapting rules:
- Paths: replace absolute laptop paths with VPS paths
- Tools: remove GUI-specific rules
- Memory: add rules for using `memory/YYYY-MM-DD.md`

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
