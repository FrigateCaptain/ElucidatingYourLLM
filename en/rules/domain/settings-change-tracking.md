# Settings Change Tracking — Documenting Configuration Changes

**Domain rule.** Apply after changing any settings.

---

## Rule [MANDATORY]

After changing any settings (OS, applications, servers, network configurations) — record the changes in the corresponding documentation files.

## What to Record

- OS settings (gsettings, systemd, cron)
- Application settings (editors, browsers, AI tools)
- Server configurations (Docker, nginx, proxy, etc.)
- Network settings (proxy, VPN, routes, firewall)
- Environment variables (`.bashrc`, `.profile`)

## Where to Record

- In the project's `FACTS.md` — if it's a key fact (IP, port, path, credentials)
- In a dedicated document — if the setting relates to a specific topic
- In the script's spec file — if the setting affects script behavior

## Format

- What was changed (specific parameter, value "was → became")
- Update the document's last-updated date
