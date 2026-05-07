# Phishing Incident Response Playbook

## Objective

This playbook provides a structured incident response workflow for handling phishing email incidents in a Security Operations Center (SOC) environment.

The goal is to standardize the investigation, containment, escalation, and recovery process when a suspicious phishing email is reported.

---

## Scenario

A user reports receiving a suspicious email requesting credential verification through a login link.

Potential risks include:

- Credential theft
- Malware delivery
- Unauthorized access
- Business email compromise

---
## Incident Workflow

<img width="1173" height="627" alt="phishing_incident_workflow png" src="https://github.com/user-attachments/assets/f2793ae5-3137-4509-be3c-032111311c67" />

---

## Detection & Initial Triage

### Indicators of Phishing

- Suspicious sender domain
- Urgent or alarming language
- Credential harvesting links
- Unexpected attachments
- Misspelled domains or typosquatting

### Initial Questions

- Did the user click the link?
- Was an attachment downloaded or opened?
- Were credentials submitted?
- Was MFA enabled?

---

## Investigation Steps

### 1. Email Header Analysis

Review the following:

- Return-Path
- SPF
- DKIM
- DMARC
- Received headers
- Sender IP address

Key indicators:

- SPF fail
- DKIM fail
- Sender domain mismatch
- Suspicious relay path

---

### 2. URL Analysis

Analyze all URLs included in the email.

Check for:

- Suspicious domains
- URL redirects
- URL shortening services
- Typosquatting

Tools:

- VirusTotal
- URLScan
- WHOIS lookup

---

### 3. Attachment Analysis

If attachments exist, review:

- File type
- File hash
- Macro presence
- Executable content

Check for:

- .exe
- .zip
- .js
- Office macros

Recommended actions:

- Hash reputation lookup
- Sandbox analysis

---

### 4. IOC Collection

Collect all relevant indicators of compromise:

- Sender email address
- Sender IP
- Domains
- URLs
- File hashes

---

## Logs to Review

Review the following logs:

### Email Security Logs
- Email gateway logs
- Mail server logs

### Network Logs
- DNS logs
- Proxy logs
- Firewall logs

### Endpoint Logs
- EDR logs
- Process creation logs
- PowerShell logs

### Authentication Logs
- Failed logins
- Successful logins
- MFA events

Key checks:

- DNS requests to malicious domains
- Proxy connections to suspicious URLs
- New suspicious process execution
- Abnormal authentication attempts

---

## Containment Actions

If malicious activity is confirmed:

- Block malicious sender
- Block malicious domain
- Block URLs at proxy/firewall
- Isolate affected endpoint
- Reset compromised credentials
- Revoke active sessions

---

## Eradication & Recovery

Recovery actions:

- Remove malicious email from all mailboxes
- Delete malicious files
- Reimage endpoint if required
- Validate system health
- Re-enable user access after remediation

---

## Escalation Criteria

Escalate to Tier 2 / Incident Response Team if:

- Credentials were submitted
- Malware executed successfully
- Multiple users received the email
- Privileged accounts were targeted
- Data exfiltration suspected

---

## Severity Classification

### Low
- Email received but no interaction

### Medium
- Link clicked or attachment opened

### High
- Credentials submitted or malware executed

---

## Lessons Learned

Post-incident improvements:

- Improve phishing awareness training
- Strengthen email filtering rules
- Block newly identified IOCs
- Review MFA enforcement

---

## Conclusion

This playbook demonstrates a structured phishing incident response workflow aligned with SOC operations.

It covers triage, investigation, containment, escalation, recovery, and lessons learned for phishing-related incidents.
