# Excel Files — Working with Excel via openpyxl

**Domain rule.** Apply when working with `.xlsx`, `.xls`.

Globs: `**/*.xlsx, **/*.xls`

---

## Excel Files Rules [MANDATORY]

When modifying existing Excel files:

1. **Load** via `openpyxl.load_workbook()` — NEVER use `Workbook()`
2. **Do not change formatting** of existing cells unless explicitly requested
3. **Modify only the specified cells** — leave the rest untouched
4. **Save under a new name** with a version suffix appended
5. **When in doubt** — ask before making changes

Formatting:
- Dates — in proper Excel format
- Table headers — bold
