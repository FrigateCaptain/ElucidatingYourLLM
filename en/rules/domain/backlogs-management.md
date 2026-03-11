# Backlogs Management — Managing Task Backlogs

**Domain rule.** Apply when creating and maintaining task backlogs.

---

## Storage

- Keep backlogs in a dedicated project folder (e.g., `backlogs/`)
- Maintain a backlog registry: a single list of all backlogs with their scope and open task count

## Creating a New Backlog

1. Create file `{name}_backlog.md` (name in English, snake_case)
2. File structure:
   - Title and brief scope description (1 sentence)
   - `## Open Tasks` section — checklist `- [ ]`
   - `## Completed Tasks` section — moved from open, with `- [x]`
   - Creation and last-updated dates at the bottom
3. Add an entry to the backlog registry
4. Update the registry's last-updated date

## Task Format

```markdown
- [ ] **Short task title**
  Description: what needs to be done and why (1–3 sentences).
  Reference: [path/to/file.md]
```

- Each task — one checkbox with a bold title
- Description — on the next line, indented (2 spaces)

## Working with Tasks

**Adding:** add to Open Tasks, update the count in the registry and last-updated dates.

**Completing:** move to Completed Tasks, change `- [ ]` to `- [x]`, add date: `*(completed: March 9, 2026)*`, update count.

**Cancelling:** move to Completed Tasks with note `*(cancelled: date — reason)*`.

## When to Create a New Backlog

- The task area **does not overlap** with existing backlogs
- Tasks share a **common theme** describable in one sentence
- If a task feels out of place in an existing backlog — that's a signal to create a new one
