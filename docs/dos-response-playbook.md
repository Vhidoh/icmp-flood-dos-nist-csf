# DoS / DDoS Response Playbook

**Purpose:** Give any responder a repeatable, calm process for an ICMP flood or any volumetric DoS / DDoS attack.
**Use with:** [incident-report-analysis.md](incident-report-analysis.md)
**Test:** Tabletop quarterly, live drill at least annually in a lab segment.

---

## 1. Roles

| Role | Responsibilities |
| --- | --- |
| Incident Commander | Declares incident, coordinates team, approves major actions like blocking traffic or taking services offline |
| Network / Security Lead | Verifies attack, applies firewall / IDS/IPS filters, engages ISP, preserves logs |
| Communications Lead | Internal staff updates, client updates, management updates |
| Management Sponsor | Approves external communications, authorises spend for mitigation, liaises with legal if needed |

If you are alone, work through the roles in order. Do not skip communications.

## 2. First 5 Minutes - Verify

1. Confirm it is a DoS, not a hardware failure or ISP outage.
   - Check: Are multiple services failing at once? Is ICMP volume / bandwidth spiking? Are firewall / monitoring graphs showing a flood?
2. Capture a snapshot: screenshot of monitoring dashboard, current firewall rule set, top talkers.
3. Open an incident log. Record time, who is responding, and every action.
4. Notify Incident Commander and Communications Lead.

**Do NOT** reboot the firewall or clear logs before capturing evidence.

## 3. Containment - Minutes 5 to 30

1. **Block / rate-limit at the edge:**
   - Confirm the ICMP rate-limit rule is active.
   - If the flood is from a small set of sources, block those sources temporarily.
   - If spoofed, rely on source IP verification and IDS/IPS filtering, not source blocking alone.
2. **Preserve capacity:**
   - Take non-critical services offline if needed to protect critical services.
   - Prioritise: client-facing web / design systems, file storage, communications.
3. **Engage upstream:**
   - Contact ISP. Provide: time attack started, traffic type (ICMP), approximate volume, and what you have already blocked.
   - Ask if ISP can apply upstream filtering or blackholing / scrubbing.
   - If you have cloud DDoS mitigation, engage it now.
4. **Communicate internally:**
   - Short update: "We are experiencing a network attack. Critical services are being restored first. Next update in 30 minutes."
   - Tell staff what NOT to do: do not reboot devices, do not share speculation externally.

## 4. Eradication - Minutes 30 to 120

1. Confirm filters are holding: ICMP volume down, latency normal, legitimate traffic flowing.
2. Check for secondary issues: Are any hosts still overwhelmed? Is any config change needed?
3. Review IDS/IPS alerts for any other suspicious traffic that may have used the flood as a distraction.
4. Do NOT declare "all clear" until monitoring shows normal baseline for at least 30 minutes.

## 5. Recovery - After Containment

1. Restore services in priority order from the recovery plan. See [incident-report-analysis.md](incident-report-analysis.md) - Recover.
2. Verify each service: log in, test a client workflow, check file integrity.
3. Return non-critical services in phases, with checks between phases.
4. Monitor closely for 48 to 72 hours for a repeat flood.
5. Communicate: "Normal service has resumed. Here is what was affected and whether any deadlines will shift."

## 6. Post-Incident - Within 5 Business Days

1. Hold a post-incident review. Invite all responders.
2. Answer: What worked? What was slow? What was missing? What will we change?
3. Update this playbook, the firewall baseline, and the monitoring thresholds.
4. File evidence: logs, PCAPs, timeline, communications.
5. Track actions in [remediation-checklist.md](remediation-checklist.md) until closed.

## 7. Communications Templates

### Internal - Initial

> Subject: Network incident - update
> We are responding to a network attack that is affecting internal services. Critical services are being restored first. Please do not reboot your device unless asked to. Next update in 30 minutes.

### Client - During

> Subject: Brief delay to [project / campaign] - we are resolving a network issue
> We are experiencing a temporary network issue that may delay [deliverable] by [time]. No client data has been affected. We will update you by [time] with a revised timeline.

### Client - After

> Subject: Resolved - [project / campaign] timeline
> The network issue is resolved and normal service has resumed. [Deliverable] is now due [new date / on track]. Thank you for your patience. If you have questions, contact [name].

## 8. When to Escalate

Escalate to management / legal / law enforcement if:

- Attack lasts more than 2 hours despite mitigation
- You suspect data breach or lateral compromise, not just availability
- You receive a ransom or extortion message
- ISP cannot mitigate and you need cloud scrubbing or law enforcement support

---

**Remember:** Stay calm, log everything, communicate early, and do not guess about attribution in client messages.
