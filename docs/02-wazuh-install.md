# Phase 2 — Wazuh All-in-One Install (Ubuntu)

## Outcome
- Dashboard accessible over HTTPS
- Manager agent (ID 000) active/local
- Alerts confirmed in `/var/ossec/logs/alerts/alerts.json` (dpkg + SCA + manager events)

## Validation Notes
- Temporary indexer connector warnings observed during first startup; later resolved.
- SCA baseline executed (CIS Ubuntu 22.04) and produced summary alert.
