# SOC Runbook – macOS LaunchAgent Persistence Alert

## Alert Description
This alert triggers when a LaunchAgent or LaunchDaemon file is created or modified
on a monitored macOS endpoint.

---

## Why This Alert Matters
LaunchAgents are a common persistence mechanism used by:
- Commodity malware
- Red team tooling
- Targeted macOS threats

Early identification can prevent long-term compromise.

---

## Initial Triage Steps
1. Identify the modified file path
2. Review the `ProgramArguments` field
3. Look for high-risk patterns:
   - curl | bash
   - wget
   - Execution from /tmp or user-writable directories
   - Unsigned or unknown binaries

---

## Validation Steps
- Confirm file creation/modification time
- Correlate with user login or install activity
- Check code signing status of referenced binaries
- Determine whether persistence was user-initiated

---

## False Positive Guidance
Common benign causes include:
- Software auto-updaters
- Developer tooling
- MDM configuration changes
- Package manager installs

If behavior aligns with known software activity, document and close.

---

## Escalation Criteria
Escalate if any of the following are observed:
- Network-based script execution
- Persistence created outside user context
- Repeated recreation after removal
- Indicators of command-and-control activity

---

## Containment Guidance
- Disable the LaunchAgent (do not delete immediately)
- Preserve file contents for investigation
- Isolate endpoint if part of broader activity
- Coordinate with endpoint or IR teams as needed

---

## Evidence to Preserve
- LaunchAgent file contents
- Wazuh alert details
- Related process execution logs
- Network telemetry (if available)
