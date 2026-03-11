# Pre-Installation Compatibility Check

**Core domain rule.** Apply before any software installation.

alwaysApply: true

---

## Pre-Installation Compatibility Check [MANDATORY]

**Before installing any application or package — verify compatibility with the target system.**

1. **Determine application requirements**:
   - Minimum OS version
   - Required libraries (GLIBC, libstdc++, etc.)
   - Architecture (x86_64, ARM, etc.)
   - Dependencies (runtime, frameworks)

2. **Determine target system parameters**:
   - OS version: `lsb_release -a` or `cat /etc/os-release`
   - GLIBC version: `ldd --version | head -1`
   - Architecture: `uname -m`

3. **Compare and decide**:
   - Compatible → proceed with installation
   - **Incompatible** → stop, report the conflict, and suggest alternatives:
     - An older/compatible version
     - Container (Docker, Flatpak, AppImage)
     - System upgrade (if acceptable)

4. **Sources of information**:
   - Release page (GitHub Releases, changelog)
   - Official documentation
   - Web search: `"[app name] [version] system requirements linux"`

**Reason**: Installing incompatible software → errors like `GLIBC_2.36 not found`, wasted time.
