# Multiple Failed Windows Logons

## Detection Objective

Detect accounts experiencing repeated Windows logon failures that may indicate password spraying, brute-force attacks, or unauthorized authentication attempts.

---

## Data Source

SecurityEvent

---

## Event ID

4625 – Failed Logon

---

## Detection Logic

The query identifies accounts generating ten or more failed authentication attempts and records:

- Account name
- Target computer
- Number of failed logons
- First observed event
- Last observed event

---

## MITRE ATT&CK

Tactic:
Credential Access (TA0006)

Technique:
Brute Force (T1110)

---

## Validation

The query successfully detected multiple accounts with repeated failed authentication attempts.

Example observations included:

- Administrator
- admin
- VADMIN
- SHIR-Hive\admin

These events demonstrate that the detection logic successfully identifies abnormal authentication activity.

---

## Status

Validated

Ready for Analytics Rule implementation.
