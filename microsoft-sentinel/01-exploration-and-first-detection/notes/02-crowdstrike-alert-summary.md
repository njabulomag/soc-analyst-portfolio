# Step 2 – Explore CrowdStrike Endpoint Data

## Objective

Review CrowdStrike endpoint alerts to understand the types of threats detected and identify the MITRE ATT&CK tactics involved.

## Query Used

See:

`queries/02-crowdstrike-alert-summary.kql`

## Key Findings

The query returned multiple high-priority endpoint alerts. Several alerts were classified as **Critical**, indicating serious security events requiring investigation.

Examples include:

- Malicious PowerShell – Critical – Execution
- Credential Dumping – Critical – Credential Access
- Sensitive File Staging – Medium – Collection
- Security Tool Tampering – High – Defense Evasion
- C2 Beacon Detected – Critical – Command and Control

The variety of MITRE ATT&CK tactics suggests that the environment contains evidence of a multi-stage attack rather than a single isolated event.

## Evidence

Screenshot:

`02-crowdstrike-alert-summary.png`
