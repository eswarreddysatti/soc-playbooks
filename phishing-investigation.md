# Phishing Investigation Playbook

## Objective

Investigate suspicious phishing emails and determine whether they are malicious.

## Investigation Steps

### 1. Collect Email Information

- Sender email address
- Subject line
- Recipient
- Timestamp

### 2. Review Email Headers

Look for:

- Sender IP
- SPF results
- DKIM results
- DMARC results

### 3. Check Indicators of Compromise

Review:

- URLs
- Domains
- Attachments
- File hashes

### 4. Threat Intelligence Check

Validate indicators using:

- VirusTotal
- AbuseIPDB
- URLScan

### 5. Determine Impact

Identify:

- Users affected
- Credentials exposed
- Malware execution

## Escalation Criteria

Escalate immediately if:

- Credential harvesting is confirmed
- Malware attachment exists
- Multiple users received the email

## Mitigation

- Block sender
- Block domains
- Remove emails from mailboxes
- Reset compromised credentials

## MITRE ATT&CK

- T1566 - Phishing
