# Detections

This directory contains custom Wazuh decoders and rules developed as part of the
Wazuh Detection Engineering Lab.

The focus of this lab is **high-signal detection design and operational quality**
rather than volume of rules.

## Current Detections

### Sudo Wrapper Abuse
- Custom rule validating misuse of `sudo` via wrapper scripts
- MITRE ATT&CK: T1110.001
- Status: Implemented and validated

### macOS LaunchAgent Persistence
- Syscheck-based visibility into LaunchAgents and LaunchDaemons
- Focus on analyst review of `ProgramArguments`
- Status: Visibility implemented; detection logic intentionally limited

## Design Notes

- Some detections rely on **analyst interpretation** rather than strict rule logic
- Brittle string-matching rules (e.g., `syscheck.diff`) were intentionally avoided
- Detection quality and tuning are addressed in Phase 5.2

## Folder Structure

- `rules/` – Custom Wazuh rules (minimal by design)
- `decoders/` – Custom decoders (added only when necessary)
