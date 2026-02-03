# wazuh-detection-engineering-lab
Hands-on Wazuh detection engineering lab using Ubuntu 22.04 and macOS agents. Covers host hardening, SIEM deployment, endpoint onboarding, alert validation, MITRE ATT&amp;CK mapping, and SOC runbook creation.

# Wazuh Detection Engineering Lab (DigitalOcean)

## Goal
Build a simple, portfolio-grade lab focused on **Wazuh**, **log ingestion**, and **detection engineering** (not complex infrastructure).

## Lab Design (Intentionally Simple)
- **1x DigitalOcean Droplet**: Ubuntu 22.04 LTS, 2 vCPU, 8 GB RAM, 80 GB SSD
- Direct SSH access from Windows (PuTTY)
- Wazuh all-in-one install (Manager + Indexer + Dashboard)
- macOS endpoint agent enrolled (Intel Mac)
- No Kubernetes, no Terraform, no multi-node clustering, no mid-build upgrades

## Why This Lab
This lab is designed to practice real SOC / Detection Engineer work:
- validate telemetry sources
- tune signal vs noise
- write custom rules
- map detections to MITRE ATT&CK
- write SOC runbooks

---

## Architecture
Windows (PuTTY) -> SSH -> Ubuntu Wazuh All-in-One
macOS Wazuh Agent -> Wazuh Manager (1514/tcp, 1515/tcp)
Dashboard via HTTPS (443/tcp)

See: `docs/00-architecture.md`

---

## Phase 1 — Host Hardening (Completed)
Hardening performed before installing Wazuh:
- Non-root admin user (`socadmin`)
- SSH hardened (no root login, no password auth, AllowUsers)
- UFW enabled (22, 443, 1514, 1515 only)
- Logging verified (rsyslog, auth.log/syslog)
- Time sync enabled (chrony)
- Baseline captured (RAM, disk, listening ports)

Docs:
- `docs/01-hardening.md`

---

## Phase 2 — Wazuh Install (Completed)
- Wazuh all-in-one installed successfully
- Dashboard accessible
- Verified alerts generated (alerts.json contains dpkg + SCA + manager events)

Docs:
- `docs/02-wazuh-install.md`

Screenshots:
- Add sanitized images under `docs/screenshots/`

---

## Phase 3 — macOS Agent Enrollment (Completed)
Key outcomes:
- macOS Wazuh agent installed (Intel64 pkg)
- launchd service loaded and running
- Agent enrolled to manager
- Duplicate stale agent removed (CLI)
- Endpoint now reporting as Active in dashboard

Docs:
- `docs/03-macos-agent.md`

---

## Next: Phase 4 — Detection Engineering
Planned work:
- Create first custom macOS detection rule
- Map to MITRE ATT&CK
- Validate alerts + tune noise
- Create SOC-style runbook

(Phase 4 work will live under `detections/` and `runbooks/`.)