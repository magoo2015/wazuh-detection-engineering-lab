# Architecture

## Components
- Ubuntu 22.04 droplet running Wazuh all-in-one:
  - Wazuh Manager
  - Wazuh Indexer (OpenSearch)
  - Wazuh Dashboard
  - Filebeat
- macOS endpoint running Wazuh agent
- Windows workstation used for SSH administration (PuTTY)

## Network Ports (UFW Allowed)
- 22/tcp: SSH admin access
- 443/tcp: Dashboard
- 1514/tcp: Agent event channel
- 1515/tcp: Agent enrollment/registration

## Security Rationale
- Minimal public exposure reduces attack surface and reduces noise.
- SSH hardened to produce clean auth telemetry for detections.
- Time sync ensures correct alert timelines and correlation.
