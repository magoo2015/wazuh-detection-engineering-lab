# Wazuh Detection Engineering Lab – Roadmap
Security Engineer / SRE Learning Track

This lab is designed to build hands-on detection engineering skills while progressively layering in
security engineering, SIEM tuning, SOC operations, and AI-assisted workflows.

The goal is to demonstrate not just detections, but sound engineering judgment, operational thinking,
and clear documentation suitable for regulated environments.

---

## Completed Phases

### Phase 1–3: Environment & Baseline
- Single-node Wazuh deployment on DigitalOcean
- Hardened Linux host
- macOS agent enrollment
- Baseline log ingestion and visibility

### Phase 4.1: Privilege Abuse Detection
- Custom sudo wrapper detection
- MITRE ATT&CK: T1110.001
- Validated rule execution and alerting

### Phase 4.2: macOS Persistence Visibility
- Syscheck monitoring for:
  - ~/Library/LaunchAgents
  - /Library/LaunchAgents
  - /Library/LaunchDaemons

### Phase 4.3: High-Signal Persistence Analysis
- Validated real-world malicious patterns (e.g., curl | bash)
- Identified Wazuh limitation with syscheck.diff matching
- Documented engineering decision to avoid brittle detections

---

## Current Phase

### Phase 5.1: Security Control Operationalization
**Goal:**  
Turn detections into maintainable, production-grade security controls with documented intent,
limitations, and SOC triage workflows.

**Deliverables:**
- Security control design documentation
- Detection limitation and tuning rationale
- SOC runbooks for high-signal alerts

---

## Upcoming Phases

### Phase 5.2: SIEM Tuning & Detection Quality
- False positive analysis
- Detection confidence and severity
- Reliability considerations

### Phase 5.3: AI-Assisted SOC Workflows
- Prompt design for analyst assistance
- AI output evaluation and refinement
- Safe human-in-the-loop decision support
