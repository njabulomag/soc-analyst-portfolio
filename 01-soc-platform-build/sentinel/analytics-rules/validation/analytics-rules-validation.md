# Analytics Rules Validation

## Validation Objective

Validate that Microsoft Sentinel Analytics Rules are correctly configured, enabled, and capable of generating security alerts and incidents.

---

## Built-in Rule Validation

The following Microsoft Sentinel analytics rules were verified as enabled:

| Rule | Status | Validation |
|------|--------|------------|
| AWS Config Service Resource Deletion Attempts | Enabled | Verified |
| Suspicious AWS CLI Command Execution | Enabled | Verified |
| NRT Security Event Log Cleared | Enabled | Verified |
| Scheduled Task ... | Enabled | Verified |

---

## Custom Rule Validation

Rule Name:

Multiple Failed Windows Logons

Validation Status:

Successfully deployed.

Data Source:

SecurityEvent

Detection Logic:

Windows Security Event ID 4625

Validation Query:

The detection query successfully identified multiple accounts with repeated failed authentication attempts.

Example Results:

- ADMINISTRATOR
- admin
- administrator
- VADMIN
- SHIR-Hive\admin

Validation Outcome:

The custom detection successfully identified abnormal authentication activity within the SecurityEvent table and is ready to generate Microsoft Sentinel alerts when the configured conditions are met.

---

## Evidence

Validation was performed using:

- Analytics Rules Overview
- Built-in Analytics Rule Configuration
- KQL Query Validation Results
- Analytics Rule Configuration
- Analytics Rule Review
- Analytics Rule Deployment

---

## Result

Analytics Rules implementation completed successfully.

The Microsoft Sentinel environment is capable of detecting suspicious Windows authentication activity using both built-in and custom analytics rules.
