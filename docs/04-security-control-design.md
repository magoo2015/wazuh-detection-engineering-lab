# Security Control Design – macOS Persistence via LaunchAgents

## Control Intent
Provide visibility into potential persistence mechanisms on macOS systems by monitoring
LaunchAgents and LaunchDaemons for suspicious or unauthorized modifications.

This control is designed to surface high-risk persistence behaviors while preserving analyst
judgment and minimizing false positives.

---

## Threat Model
Adversaries frequently use LaunchAgents and LaunchDaemons to achieve persistence on macOS,
executing malicious binaries or scripts at user login or system startup.

**MITRE ATT&CK Techniques:**
- T1543 – Create or Modify System Process
- T1547 – Boot or Logon Autostart Execution
- T1059 – Command and Scripting Interpreter
- T1105 – Ingress Tool Transfer

---

## Telemetry Source
- Wazuh Syscheck (File Integrity Monitoring)

**Monitored Paths:**
- ~/Library/LaunchAgents
- /Library/LaunchAgents
- /Library/LaunchDaemons

---

## What This Control Does Well
- Detects creation or modification of persistence artifacts
- Provides file content diffs for analyst review
- Surfaces early-stage persistence behaviors
- Enables detection without invasive host actions

---

## Known Limitations
- `syscheck.diff` content is not reliably matchable via Wazuh rule logic
- Detection requires analyst interpretation of `ProgramArguments`
- Legitimate software updates and developer tools may trigger alerts

---

## Design Decisions
- Avoided brittle string-matching rules on diff output
- Prioritized analyst-driven validation over automation
- Accepted investigative alerts in exchange for higher signal quality

---

## Non-Goals
- This control does **not** block execution
- This control does **not** auto-remediate
- This control does **not** guarantee malicious intent

---

## Operational Ownership
- Owned by Security Engineering
- Reviewed quarterly or after major macOS updates
- Tuning decisions documented rather than silently changed

---

## Risk Considerations
Failure to monitor persistence mechanisms may allow:
- Long-term access by attackers
- Credential harvesting
- Follow-on lateral movement

This control reduces dwell time by improving early detection.
