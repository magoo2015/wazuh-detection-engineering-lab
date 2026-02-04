# Phase 4 — Detection Engineering (Completed)

## Objective
Design, implement, and validate a **custom macOS detection** in Wazuh using real endpoint telemetry, aligned to **MITRE ATT&CK** and documented with **SOC-ready context**.

---

## Environment
- **Platform:** DigitalOcean  
- **OS:** Ubuntu 22.04  
- **Wazuh Version:** 4.14.2 (all-in-one: manager, indexer, dashboard)  
- **Endpoint:** macOS (Intel)  
- **Agent Version:** 4.14.2  

---

## Detection Implemented
**macOS – Possible Password Guessing via Repeated sudo Authentication Failures**

- **Trigger Source:** macOS Unified Logs (`sudo`)
- **Base Rule:** Wazuh built-in rule `5404`  
  - *“Three failed attempts to run sudo”*
- **Custom Wrapper Rule:** `100100`

---

## Custom Rule Details
- **Rule ID:** `100100`
- **Severity:** Level 10
- **MITRE ATT&CK:**
  - `T1110.001 – Password Guessing` (Credential Access)

### Logic
- Chain off Wazuh’s native macOS sudo detection (`if_sid=5404`)
- Add SOC-friendly context, grouping, and MITRE mapping
- Preserve vendor rule logic while extending it safely

### Rule Location
```text
/var/ossec/etc/rules/local_rules.xml
