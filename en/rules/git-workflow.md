# Git Workflow — Git Rules

---

## Git Workflow [MANDATORY]

**For the AI assistant:**
- **NEVER do a git push** without explicit user confirmation
- **NEVER commit changes** until the user indicates the work is complete
- **NEVER assume the user's email** — ask explicitly
- **NEVER edit the main rules file** without an explicit request
- When the user's focus shifts — suggest committing previous work
- Suggest commits when a set of changes is ready
- Wait for approval before pushing

## Repository Registry [CANONICAL]

Maintain a dedicated registry file for all project repositories, listing: local path, remote URL, branch, and auto-sync status.

**Consult the registry** for any remote operations (push, pull, clone, set-url).  
**Update the registry** when: adding a new repository, renaming, changing remote URL, or modifying auto-sync settings.

## Connecting a New Repository

1. Initialize git: `git init`
2. Add remote via SSH: `git remote add origin git@github.com:<username>/<repo>.git`
3. Create `.gitignore` (exclude: `*.log`, service directories)
4. First commit and push: `git add . && git commit -m "..." && git push -u origin main`
5. Set up auto-sync if needed (systemd user services)
6. **Update the repository registry**
