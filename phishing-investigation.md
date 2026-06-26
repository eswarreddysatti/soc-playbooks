# Phishing Investigation Playbook

## Overview

This playbook provides a standardized process for investigating phishing incidents within an enterprise Security Operations Center (SOC).

### Severity Classification

| Severity | Description                                  |
| -------- | -------------------------------------------- |
| Low      | Spam or benign phishing attempt              |
| Medium   | User interaction occurred                    |
| High     | Credential theft suspected                   |
| Critical | Malware execution or multiple users affected |

---

# MITRE ATT&CK Mapping

| Technique | Description                       |
| --------- | --------------------------------- |
| T1566     | Phishing                          |
| T1204     | User Execution                    |
| T1059     | Command and Scripting Interpreter |
| T1078     | Valid Accounts                    |

---

# Phase 1: Detection

## Sources

* User reported email
* Microsoft Defender
* Secure Email Gateway
* Splunk Alert
* CrowdStrike Alert

## Initial Questions

* Who received the email?
* How many recipients?
* Did anyone click?
* Was an attachment opened?

---

# Phase 2: Triage

## Gather Artifacts

### Email Details

* Sender
* Recipient
* Subject
* Message-ID
* Timestamp

### Indicators

* URLs
* Domains
* Attachments
* Hashes
* IP Addresses

---

# Phase 3: Investigation

## Header Analysis

Review:

* SPF
* DKIM
* DMARC

Check for:

* Sender spoofing
* Domain impersonation
* Reply-to mismatch

## URL Analysis

Validate URLs using:

* VirusTotal
* URLScan
* AbuseIPDB

## Attachment Analysis

Review:

* SHA256 hash
* File type
* Macro execution
* Sandbox results

---

# Phase 4: Containment

## Immediate Actions

* Quarantine email
* Block sender
* Block domains
* Block URLs
* Disable compromised accounts

---

# Phase 5: Eradication

Remove:

* Malicious emails
* Persistence mechanisms
* Malware artifacts

Reset:

* Passwords
* Tokens
* Sessions

---

# Phase 6: Recovery

Verify:

* User account integrity
* Endpoint health
* Mail flow

Monitor:

* Authentication activity
* Endpoint detections

---

# Phase 7: Lessons Learned

Document:

* Root Cause
* Impact
* Indicators of Compromise
* Detection Gaps
* Recommended Improvements

---

# Splunk Queries

## Failed Login Spike

index=* EventCode=4625
| stats count by user

## Suspicious PowerShell

index=* powershell
| search "-enc"

---

# References

* NIST SP 800-61 Incident Response Lifecycle
* MITRE ATT&CK T1566 (Phishing)
