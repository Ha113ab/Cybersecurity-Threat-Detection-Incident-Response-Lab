# Cybersecurity Threat Detection & Incident Response Lab

**Author:** Haileab T. Bekele
**Dates:** September 2025 – November 2025
**Time:** 30 hours
**Status:** Simulated SOC Security Analyst lab, coursework. This is NOT production SOC employment and does NOT claim production SIEM, EDR, or SOAR experience.

Note on the name: this lab was listed as a "CySA+ hands-on project." CySA+ here is the project name, not a certification held.

## Objective
Triage simulated SOC incidents, analyze network and support signals, and document mitigation and escalation steps — in a repeatable workflow a reviewer can follow, not just a list of alerts closed.

## Simulated environment
- A simulated alert queue, with log files and packet captures provided for analysis.
- Analysis with Wireshark for packet and network signals, Linux log review, and Python scripting basics for simple log parsing and counting — the tools in the author's documented record.
- Documentation in incident reports and a triage playbook, with severity and escalation criteria applied consistently.
- No production system, no real customer data, and no live incident response is claimed.

## Triage workflow (applied to every incident)
1. **Detect:** Read the alert, note time, source, destination, and affected host or account.
2. **Analyze:** Check log entries and packet captures for corroboration. Separate a true signal from a false positive, and note what evidence is missing.
3. **Contain:** Apply the least-disruptive containment that stops the simulated activity — isolate the host or account in the scenario, block the malicious indicator in the scenario, or disable the compromised credential in the scenario.
4. **Mitigate:** Remove the simulated cause, reset the credential or close the exposure, and verify the signal stops.
5. **Document:** Write root cause, actions taken, evidence, and what would be checked next.
6. **Escalate:** Escalate by severity (below), not by guesswork.

## Severity and escalation
- **P1 — Escalate immediately:** Suspected compromise of a host or account, data exfiltration signal, or active malicious outbound traffic.
- **P2 — Escalate same shift:** Repeated failed logins with a successful login after them, or a confirmed malicious file or link opened.
- **P3 — Handle and document:** Single failed-login burst with no success, or a scan with no successful access. Document and monitor for recurrence.

## Scenarios worked
### 1. Phishing email
- Signal: User reports a suspicious email with a link.
- Analysis: Check sender, link destination, and whether the link was opened, using the lab logs and packet capture.
- Containment / mitigation: Mark the message as malicious in the scenario, block the link domain in the scenario, and reset the credential if it was entered.
- Escalation: P2, or P1 if a credential was entered or a file was downloaded.

### 2. Brute-force login
- Signal: Many failed logins for one account, followed by a successful login.
- Analysis: Count failures by source, check time pattern, and check what the account accessed after login.
- Containment / mitigation: Lock or reset the account in the scenario, block the source in the scenario, and review post-login activity.
- Escalation: P2, or P1 if post-login activity shows access to sensitive data.

### 3. Suspicious outbound traffic
- Signal: A host sends unusual outbound traffic after a download.
- Analysis: Use Wireshark to identify destination, protocol, and volume, and correlate with the download time in the logs.
- Containment / mitigation: Isolate the host in the scenario, remove the suspicious file in the scenario, and verify outbound traffic stops.
- Escalation: P1.

### 4. Internal network scanning
- Signal: One internal host scans many internal addresses and ports.
- Analysis: Identify the scanning host, the ports scanned, and whether any service responded.
- Containment / mitigation: Isolate the scanning host in the scenario, and check it for compromise before returning it to the network.
- Escalation: P2, or P1 if a service was successfully accessed.

### 5. Vulnerability follow-up
- Signal: A vulnerability report lists issues by severity for lab hosts.
- Analysis: Triage by severity and exposure — internet-facing and authenticated issues first, then internal issues, then informational findings.
- Mitigation: Document the patch or configuration fix for each issue, and the verification check that would confirm it is closed.
- Escalation: P2 for a critical internet-facing issue, P3 for lower-severity internal issues.
- Note: This scenario triages vulnerability reports provided in the lab. It does not claim production vulnerability-scanning tool experience.

## Incident report template used
Date/time, alert source, affected host/account, evidence (log and packet references), analysis, severity, containment, mitigation, root cause, escalation decision, and follow-up check.

## Outcome
- Five scenario types triaged end-to-end, each with a documented incident report.
- A reusable triage playbook: detect, analyze, contain, mitigate, document, escalate.
- Skills demonstrated: incident triage, root cause analysis, network security, Wireshark packet analysis, Linux log review, Python scripting basics for log parsing, and clear incident documentation.

## What this does NOT claim
- No production SOC employment, no live incident, and no SIEM, EDR, or SOAR production experience.
- No specific commercial SIEM product is named, because none is in the author's documented record for this lab.
