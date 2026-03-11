# File Management — Files and Documents Management

---

## File Management [MANDATORY]

- Use clear, descriptive file and folder names
- Maintain a logical organizational structure
- Group related materials together
- Regularly clean up outdated content
- Always reference real file paths
- **When in doubt — ask the user for the save path**
- **FACTS.md**: important factual information (names, links, addresses, specs) — keep in a separate file in the project folder

### Key Project Files
- `README.md` — structure and navigation
- `FACTS.md` — important facts (names, links, specs)
- `executive-summary.md` — one-page overview (optional)

---

## Literal Execution of Requests [MANDATORY]

- Make **exactly** the changes the user asks for
- **Do NOT** make unrequested changes (column order, formatting, renaming, restructuring, etc.)
- If the AI thinks an additional change would be useful — **ask for confirmation first**
- Only after explicit user confirmation — make the additional change

**Exception — scripts**: when creating or modifying executable scripts, the full Scripts Management process always applies.

### File Protection

- Work only with explicitly specified files. Do not touch other files, even if they seem similar or "logically adjacent"
- If there are multiple potential sources or any doubt remains — pause and ask the user
- Do not change the meaning, structure, or format of a document without a direct request

### Backups and Confirmations

- Before experiments or bulk edits — make a copy/backup of the original file
- Before applying edits — describe the planned changes and wait for confirmation

---

## Settings Change Tracking [MANDATORY]

After changing any settings (OS, applications, servers, network configurations) — record the changes in the corresponding documentation files.

**What to record:**
- OS and system service settings
- Application settings
- Server configurations
- Network settings (proxy, VPN, routes, firewall)
- Environment variables

**Where to record:**
- In `FACTS.md` — if it's a key fact (IP, port, path)
- In the relevant profile document — if the setting belongs to a specific topic
- In the script's spec file — if the setting affects script behavior

**Recording format:**
- What was changed (specific parameter, "old value → new value")
- Update the document's last-updated date
