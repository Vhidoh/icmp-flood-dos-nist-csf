# Remediation Checklist - 30 / 60 / 90 Days

Use this checklist to turn the incident analysis into tracked work. Tick items as they are completed and add the date and owner.

**How to use:** Copy this file into a GitHub Issue or Project, or keep it in the repo and update it via pull requests.

---

## Already Done - From the Incident

- [x] Blocked incoming ICMP to contain the flood
- [x] Took non-critical services offline to preserve capacity
- [x] Restored critical services first
- [x] Added firewall rule to limit rate of incoming ICMP
- [x] Added source IP verification to drop spoofed ICMP
- [x] Deployed network monitoring for abnormal traffic
- [x] Deployed IDS/IPS to filter suspicious ICMP

---

## 30 Days - Stabilise

### Identify
- [ ] Complete asset inventory and network diagram
- [ ] List critical vs. non-critical services and get management approval
- [ ] Document RTO / RPO for critical services

### Protect
- [ ] Confirm firewall hardening baseline is documented and applied
- [ ] Back up all firewall and network device configurations
- [ ] Document which ICMP types are allowed and why
- [ ] Enforce MFA for all firewall / network admin access
- [ ] Review who can change firewall rules, remove stale access

### Detect
- [ ] Define baseline for normal ICMP volume, bandwidth, and latency
- [ ] Set alert thresholds and confirm alerts reach the on-call analyst
- [ ] Centralise firewall, IDS/IPS, and server logs

### Respond
- [ ] Publish Incident Response plan with named roles
- [ ] Publish DoS / DDoS playbook (see dos-response-playbook.md)
- [ ] Define internal and client communication templates

### Recover
- [ ] Publish prioritised recovery order
- [ ] Confirm backups exist for configs and design / client files

---

## 60 Days - Prove It Works

### Identify
- [ ] Complete vulnerability scan and review results
- [ ] Review ISP and hosting dependencies and their DoS protection

### Protect
- [ ] Test that rate limits do not break legitimate diagnostics
- [ ] Segment network: internal, servers, DMZ, guest Wi-Fi
- [ ] Train all staff on reporting an outage / attack
- [ ] Train network admins on firewall review and DoS playbook

### Detect
- [ ] Run controlled ICMP flood test in a lab segment, verify alerts fire in under 5 minutes
- [ ] Tune IDS/IPS rules, review false positives weekly
- [ ] Build real-time network health dashboard

### Respond
- [ ] Run tabletop exercise for a DoS attack, update playbook with lessons
- [ ] Test evidence preservation: logs, PCAPs, timeline

### Recover
- [ ] Test backup restore for a critical service
- [ ] Run recovery drill for critical services

---

## 90 Days - Harden for Scale

### Identify
- [ ] Complete full risk assessment including DoS / DDoS scenario
- [ ] Update risk register with owners and mitigations
- [ ] Audit firewall rules and access privileges quarterly

### Protect
- [ ] Review ISP / cloud DDoS mitigation options and decide on upstream protection
- [ ] Patch all network devices to current firmware / software
- [ ] Review and approve policies: firewall change, acceptable use, patching, access review

### Detect
- [ ] Review MTTD and MTTR metrics, set improvement targets
- [ ] Review log retention (target 90 days) and SIEM coverage

### Respond
- [ ] Second tabletop or live drill, with external stakeholders if relevant
- [ ] Post-incident review process documented and scheduled

### Recover
- [ ] Test full recovery order end to end
- [ ] Confirm post-recovery monitoring checklist (48 to 72 hours) is in the playbook

---

## Ongoing - Every Quarter

- [ ] Audit firewall rules and configurations
- [ ] Review IDS/IPS and monitoring alerts and tuning
- [ ] Review asset inventory and critical services list
- [ ] Run tabletop exercise
- [ ] Test backup restore
- [ ] Review risk register and update owners

---

## Tracking Template

| Action | Owner | Due Date | Status | Notes |
| --- | --- | --- | --- | --- |
| Example: Publish DoS playbook | Security Lead | 2026-12-01 | Done | Link to playbook |
|  |  |  |  |  |
|  |  |  |  |  |
