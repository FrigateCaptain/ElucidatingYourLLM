# Rules Management — Managing AI Assistant Rules

**Domain rule.** Apply when creating, editing, or deleting rule files.

---

## Placement

- **Core rules** (needed in every conversation: AI behavior, safety, git, language, response format) — in the main rules file (`.cursorrules`, `CLAUDE.md`, or platform equivalent).
- **Domain rules** (for specific file types, tools, formats) — in separate files with defined scope (globs or description).
- Rules in plain `.md` files without special platform configuration are **not automatically loaded**.

## Rule File Structure

Each rule file starts with metadata (frontmatter or header):
- Description: what it applies to
- Scope: glob pattern for files, or semantic description
- `alwaysApply` flag: only if the rule is needed in **every** conversation

## Choosing Activation Type

- **`alwaysApply: true`** — only if the rule is needed in EVERY conversation. Test: "If the user asks 'what is 2+2?' — is this rule needed?" If not — use globs.
- **`globs`** — preferred for domain rules. Use specific file patterns.
- **`description` without globs** — for rules hard to tie to files; the platform loads them by semantic relevance.

## Quality Principles [MANDATORY]

- **One rule = one goal.** If a rule contains unrelated topics — split into separate files.
- **No duplication.** Each rule exists in one place. If a duplicate is found — merge.
- **Size control.** Good target: up to 50 lines. If a rule exceeds ~500 lines — suggest splitting to the user.
- **Separate rules from artifacts:**
  - **Rule** — a conditional prescription for classes of situations: "if [situation] — do [X]."
  - **Skill** — an expertise package for a specific task, loaded on demand.
  - **Analytical document / case study** — in a dedicated folder, not in rules.

## Rules Registry

Register all rules in a central registry. Update the registry when creating, modifying, or deleting a rule.

## Validation Before Saving

- File name — descriptive, kebab-case
- Metadata includes `description`, `globs`, or `alwaysApply`
- `alwaysApply: true` is justified (the "2+2" test)
- Globs are not overly broad
- Content — conditional prescriptions, not instructions/workflows
- No duplication with other rules
- If > 500 lines — suggest splitting to the user
- Rule is entered in the registry
