# Phase 3 — macOS Agent Install + Enrollment

## Situation
- Initial macOS agent state was inconsistent (stale launchd service).
- Cleaned stale launch daemon and installed the correct macOS agent package.

## Install
- Intel Mac used `wazuh-agent-4.14.2-1.intel64.pkg`
- Verified `/Library/Ossec` created and owned by root:wazuh
- Managed agent via `launchctl` (launchd)

## Enrollment
- Enrolled with `agent-auth`
- Resolved "Duplicate agent name" by removing stale/disconnected agent
- Confirmed endpoint shows Active in dashboard
