# Projects Management — Managing Projects

**Domain rule.** Apply when creating, renaming, or registering a project.

---

## Project Registry

Maintain a single registry file for all workspace projects. Update when: creating, renaming, or changing a project's or subproject's status.

## Project Folder Structure

Each project folder should contain the following files:

### README.md — navigation and entry point
- What the project is (1–2 sentences)
- Links to all files in the folder with a brief description of each
- Related projects and external resources
- Project status and date of last activity

### CONTEXT.md — background and rationale
- Background: what led to launching the project
- Why now: what made the project relevant at this time
- Stakeholders: who is invested in the outcome
- Key decision history: forks and rationale for the chosen path
- Assumptions: what is treated as true without proof

### GOALS.md — where we're going
- Main project goal (one sentence)
- Sub-goals / expected outcomes (list)
- Success criteria: how we'll know the goal is achieved
- What is NOT a goal (anti-goals) — optional

### CONDITIONS_n_CONSTRAINTS.md — working conditions
- Resources: who is involved, budget, tools
- Timeline: deadlines, key dates
- Constraints: technical, organizational, financial
- Risks: known threats and uncertainties at start

### PLAN.md — how we're getting there
- Project phases with descriptions and sequence
- Tasks within phases with statuses
- Current focus and next step

### FACTS.md — source of truth for facts
- Key facts: names, addresses, URLs, identifiers
- Decisions made, with dates
- Technical parameters: versions, configs, ports, paths
- Everything that needs to be quickly findable — mark as `[CANONICAL]`

### BACKLOG.md — deferred but not forgotten
- Tasks that didn't make it into the current plan
- Ideas to explore
- Open issues — unanswered questions

## Subprojects

**When to create**: a task with its own research context within a parent project, requiring a separate document or dialogue.

**File naming**: `{parent_number}-{sequence}_{name}` — en, kebab-case.
Example: `35-1_bilingual-repo`, `35-2_hitl-positioning`

**Storage**: `{parent_project}/subprojects/{subproject_name}.md`
