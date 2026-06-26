# Suspicious Login Investigation Playbook

## Overview

This playbook provides a standard process for investigating suspicious authentication activity, unauthorized access attempts, and compromised accounts.

---

# Severity Classification

| Severity | Description                          |
| -------- | ------------------------------------ |
| Low      | Single failed login                  |
| Medium   | Multiple failed logins               |
| High     | Successful login from unusual source |
| Critical | Confirmed account compromise         |

---

# MITRE ATT&CK Mapping

| Technique | Description              |
| --------- | ------------------------ |
| T1078     | Valid Accounts           |
| T1110     | Brute Force              |
| T1098     | Account Manipulation     |
| T1539     | Steal Web Session Cookie |

---

# Phase 1: Detection

## Alert Sources

* Splunk
* Azure AD
* Okta
* VPN Logs
* CrowdStrike Identity Protection

---

# Phase 2: Triage

Collect:

* Username
* Source IP
* Timestamp
* Location
* Device Name

Questions:

* Is the login expected?
* Is MFA enabled?
* Has the user traveled?

---

# Phase 3: Investigation

## Authentication Review

Check:

* Failed login count
* Successful logins
* MFA events
* Password resets

## Location Analysis

Review:

* Geolocation
* Impossible travel
* VPN usage

## Endpoint Analysis

Review:

* Hostname
* EDR detections
* Running processes

---

# Splunk Queries

## Failed Logins

index=* EventCode=4625
| stats count by Account_Name

## Successful Logins

index=* EventCode=4624
| stats count by Account_Name

## Login Source Analysis

index=* EventCode=4624
| stats count by src_ip

---

# Phase 4: Containment

Actions:

* Reset password
* Revoke sessions
* Disable account
* Force MFA re-registration

---

# Phase 5: Recovery

Verify:

* User identity
* Account ownership
* No persistence mechanisms

---

# Lessons Learned

Document:

* Root Cause
* Timeline
* Impact
* Security Improvements

---

# References

* NIST SP 800-61
* MITRE ATT&CK T1078
