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

### ✅ Phase 4.1 — macOS Credential Access Detection
- Implemented a custom Wazuh wrapper rule (`100100`) chained to the built-in macOS sudo rule (`5404`)
- Detects repeated failed sudo authentication attempts
- MITRE ATT&CK: **T1110.001 – Password Guessing**
- Demonstrates safe extension of vendor logic using `if_sid`

### ✅ Phase 4.2 — macOS Persistence Detection (LaunchAgents)
- Enabled File Integrity Monitoring (FIM / syscheck) for macOS persistence locations:
  - `/Users/*/Library/LaunchAgents`
  - `/Library/LaunchDaemons`
- Verified base syscheck alerts:
  - **554** — File added
  - **550** — Integrity checksum changed
- Implemented custom persistence wrapper rules:
  - **100200** — New LaunchAgent plist added
  - **100201** — Existing LaunchAgent plist modified
- Rules safely chain off base syscheck logic and add MITRE context
- MITRE ATT&CK: **T1543.001 – Launch Agent**

### ⏭️ Next: Phase 4.3 — High-Signal macOS Persistence (Pro Move)
- Detect suspicious LaunchAgent behavior (not just file changes)
- Focus on malicious plist content such as:
  - `ProgramArguments` invoking `bash`, `curl`, `python`
  - `RunAtLoad` or `KeepAlive` persistence mechanisms
  - Execution from user-writable or temporary paths