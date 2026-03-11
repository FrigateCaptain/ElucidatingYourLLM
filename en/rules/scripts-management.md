# Scripts Management — Script Lifecycle Management

---

## Scripts Management [MANDATORY]

### Script Locations

Scripts can reside in multiple directories. Define the list of script locations during deployment.

**Centralized management files** (stored in the main `scripts/` directory):
- `REGISTRY.md` — **unified registry** of all scripts across all locations
- `TRIVIAL_TASKS.md` — shared list of trivial task types
- `SPEC_TEMPLATE.md` — base spec file template
- `logs/` — unified log directory for local scripts
- `archive/` — unified directory for deprecated scripts

**All scripts created by the AI assistant [MANDATORY]**: regardless of location, **must** go through the full Scripts Management process: spec file, header, registry.

### 1. Directory Structure

```
scripts/
├── REGISTRY.md
├── TRIVIAL_TASKS.md
├── SPEC_TEMPLATE.md
├── logs/
│   └── {script_name}_{YYYYMMDD}_{HHMM}.log
├── archive/
├── {script}.py|sh
├── {script}_spec.md
└── ...
```

**Principles:**
- A script and its spec file live **side by side**, in the same directory
- `scripts/logs/` — unified log directory for all local scripts
- `scripts/archive/` — unified directory for deprecated scripts (move as a pair: script + spec)
- **When reorganizing or moving scripts [MANDATORY]**: update paths in all places:
  1. Update the "Path" column in `scripts/REGISTRY.md`
  2. Update the `SPEC:` field in the script header (if the spec file path changed)
  3. Update the "Script location" field in the spec file (if present)
  4. Update any cross-references in other documents

### 2. Spec File (Script Requirements)

**Naming**: `{script_name}_spec.md`

Example: `transcribe_video.py` → `transcribe_video_spec.md`

**Contents**: use the template from the script's directory (`SPEC_TEMPLATE_VPS.md`, `SPEC_TEMPLATE_*.md`) if available; otherwise use the base `scripts/SPEC_TEMPLATE.md`

**Required spec file elements:**
- Purpose (one sentence)
- Input (arguments, files, environment variables)
- Output (what it creates, where it writes)
- Dependencies (packages, utilities, APIs)
- Behavior (logic, error handling, constraints)
- Logging (where it logs, what it logs)
- **Control level**: `APPROVAL REQUIRED` or `TRIVIAL TASK (no approval needed)`
- **Launch mode** [CANONICAL]:
  - Type: `manual` / `auto:systemd` / `auto:cron` / `called`
  - For `auto:systemd` — service name, path to unit file
  - For `auto:cron` — cron schedule
  - For `called` — which script calls it and under what conditions
- Requirements change history (table)
- Three dates at the bottom:
  - **Requirements creation date** — never changes
  - **Requirements last updated date**
  - **Script compliance date**

### 3. Script Header (Link to Spec)

**Python:**
```python
#!/usr/bin/env python3
"""
Brief description of the script's purpose.
SPEC: script_name_spec.md
COMPLIANT: YYYY-MM-DD
LAUNCH: manual
"""
```

**Bash:**
```bash
#!/bin/bash
# Brief description of the script's purpose.
# SPEC: script_name_spec.md
# COMPLIANT: YYYY-MM-DD
# LAUNCH: manual
```

`LAUNCH:` allowed values:
- `manual`
- `auto:systemd(service.name)`
- `auto:cron(schedule)`
- `called:script_name`
- Combinations separated by commas

### 4. Script Creation Process

1. **Determine control level** — check against the `scripts/TRIVIAL_TASKS.md` list
2. **Define requirements** → write the spec file using the template
3. **If approval is required** → show the user and wait for confirmation
4. **Create the script** with the `SPEC:` + `COMPLIANT:` + `LAUNCH:` header
5. **Update `scripts/REGISTRY.md`**
6. **Set all dates** — in the spec file and the script header
7. **If auto:systemd or auto:cron** — create/update the unit file or cron entry

### 5. Script Modification Process

1. **Read the current spec file**
2. **Update requirements** in the spec file
3. **Update "Requirements last updated date"**
4. **Add an entry** to the "Requirements change history" table
5. **If approval is required** → show the user the updated requirements and wait for confirmation
6. **Apply changes to the script**
7. **Update `COMPLIANT:`** in the header and the date in the spec file
8. **Update `LAUNCH:`** if the launch mode changed
9. **Update `scripts/REGISTRY.md`**

### 6. Script Registry (REGISTRY.md)

Table columns:
- **Script** — file name
- **Path** — full relative path
- **Purpose** — one sentence
- **Language** — Python / Bash
- **Launch** — launch mode
- **Status** — active / archived / in development
- **Scope** — `system` / `project`
- **Created**

Update when: creating, changing purpose, moving, archiving, or changing the launch mode of a script.

### 7. Script Execution Logging

**Directory**: `scripts/logs/`
**Naming**: `{script_name}_{YYYYMMDD}_{HHMM}.log`

**What to log:** start time, input parameters, key stages, result, end time.

**Python — template:**
```python
import logging
from datetime import datetime
from pathlib import Path

script_name = Path(__file__).stem
log_dir = Path(__file__).parent / "logs"
log_dir.mkdir(exist_ok=True)
log_file = log_dir / f"{script_name}_{datetime.now().strftime('%Y%m%d_%H%M')}.log"

logging.basicConfig(
    level=logging.INFO,
    format="%(asctime)s [%(levelname)s] %(message)s",
    handlers=[
        logging.FileHandler(log_file, encoding="utf-8"),
        logging.StreamHandler()
    ]
)
```

**Bash — template:**
```bash
SCRIPT_NAME=$(basename "$0" .sh)
LOG_DIR="$(dirname "$0")/logs"
mkdir -p "$LOG_DIR"
LOG_FILE="$LOG_DIR/${SCRIPT_NAME}_$(date +%Y%m%d_%H%M).log"
log() { echo "$(date '+%Y-%m-%d %H:%M:%S') [$1] $2" | tee -a "$LOG_FILE"; }
log "INFO" "Start: $0 $*"
```

### 8. Trivial Tasks List

**File**: `scripts/TRIVIAL_TASKS.md`

Contains a list of task types/categories for which the spec file is created **without user confirmation**. Only expanded after explicit user agreement (see section 4, step 1).

### 9. Post-Modification Self-Check [CRITICAL]

| # | Item | Done? |
|---|------|-------|
| 1 | Current spec file was read before starting work | |
| 2 | Requirements in the spec file are updated | |
| 3 | "Requirements last updated date" is updated | |
| 4 | Entry added to the "Change history" table | |
| 5 | Approval obtained (if "APPROVAL REQUIRED") | |
| 6 | Changes applied to the script | |
| 7 | `COMPLIANT:` updated in the header + date in spec file | |
| 8 | `LAUNCH:` updated (if launch mode changed) | |
| 9 | `scripts/REGISTRY.md` updated | |

**Rules:**
- The checklist is filled in the **TODO list or in the response to the user** — before moving to the next task
- If any item is not completed — **stop and complete it** before moving on
- Item 9 (REGISTRY.md) is **always** mandatory, even if changes seem minor — at least update the date

### 10. Requirements Approval ≠ Plan Approval [CRITICAL]

**Approving an action plan does NOT substitute for approving the spec file (requirements).**

- If the script has control level `APPROVAL REQUIRED`:
  1. **First** update the spec file with new requirements
  2. **Then** show the user **the specific changes in the spec file** and explicitly ask: "Are the requirements in the spec file correct? Can I proceed with implementation?"
  3. **Only after explicit confirmation** — proceed with modifying the script code
- User agreement on a plan, strategy, architecture, or step description is **not** considered requirements approval
- Requirements approval is confirmation of **the specific content of the spec file** after it has been updated
