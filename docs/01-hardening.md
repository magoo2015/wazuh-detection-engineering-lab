# Phase 1 — Host Hardening (Ubuntu 22.04)

## Actions
1. Created non-root admin user: `socadmin`
2. Hardened SSH:
   - PermitRootLogin no
   - PasswordAuthentication no
   - AllowUsers socadmin
3. Enabled UFW with minimal inbound ports (22/443/1514/1515)
4. Verified logging (rsyslog, auth.log, syslog)
5. Enabled time sync (chrony)
6. Captured baseline:
   - free -m
   - df -h
   - ss -tuln

## Why it matters
- Least privilege admin model is SOC standard
- SSH changes reduce brute-force risk and produce high-signal auth logs
- Firewall enforces intentional exposure
- Time sync preserves alert fidelity for investigations
