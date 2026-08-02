# Microsoft Sentinel Project 03 – Enterprise SOC Investigation

## Project Overview

This project demonstrates a realistic Security Operations Center (SOC) investigation using Microsoft Sentinel and Microsoft Defender XDR.

The investigation validates enterprise security data sources and correlates endpoint, identity, firewall, and operating system telemetry to identify suspicious activity using Kusto Query Language (KQL).

---

## Objectives

- Validate connected security data sources.
- Investigate endpoint security alerts.
- Analyze firewall activity.
- Review identity authentication events.
- Correlate events across multiple security products.
- Document findings using KQL, screenshots, and investigation notes.

---

## Skills Demonstrated

- Microsoft Sentinel
- Microsoft Defender XDR
- Kusto Query Language (KQL)
- Threat Hunting
- SOC Investigation
- Event Correlation
- Detection Engineering
- Microsoft Entra ID
- CrowdStrike Falcon
- Palo Alto Firewall
- Okta Identity
- Windows Security Monitoring

---

## Data Sources

- CrowdStrike Alerts
- Microsoft Entra ID
- Okta
- Palo Alto Firewall (CommonSecurityLog)
- Windows Security Events

---

## Project Structure

```text
03-enterprise-soc-investigation/

├── README.md
├── queries/
├── screenshots/
└── notes/
```

---

# Step 1 – Validate Connected Data Sources

## Query

[01-validate-data-sources.kql](queries/01-validate-data-sources.kql)

## Evidence

![Connected Data Sources](screenshots/01-validate-data-sources.png.png)

## Findings

A KQL query was executed to validate that Microsoft Sentinel was receiving telemetry from multiple enterprise security platforms.

The investigation confirmed active telemetry from:

- CrowdStrike Alerts (53 records)
- Microsoft Entra ID (3,663 records)
- Okta (36 records)
- Palo Alto Firewall (149 records)
- Windows Security Events (23,864 records)

This confirmed that the environment contains sufficient endpoint, identity, firewall, and operating system telemetry to perform enterprise-scale SOC investigations.

---
---

# Step 2 – CrowdStrike Endpoint Investigation

## Query

[02-crowdstrike-endpoint-investigation.kql](queries/02-crowdstrike-endpoint-investigation.kql)

## Evidence

### Endpoint Alert Overview

![CrowdStrike Endpoint Overview](screenshots/02-crowdstrike-endpoint-overview.png.png)

### Critical Endpoint Alerts

![CrowdStrike Critical Alerts](screenshots/02-crowdstrike-critical-alerts.png.png)

## Findings

A KQL investigation was performed against the **CrowdStrikeAlerts** table to review endpoint detections.

The query returned **53 alerts**, including several critical detections such as Credential Dumping, Command and Control activity, Malicious PowerShell Execution, Security Tool Tampering, Sensitive File Staging, and Ransomware Behavior.

These alerts mapped to multiple MITRE ATT&CK tactics, demonstrating how Microsoft Sentinel can be used to investigate endpoint activity and understand the progression of an attack across different stages of the cyber kill chain.

---

# Step 3 – Palo Alto Firewall Investigation

## Query

[03-palo-alto-firewall-investigation.kql](queries/03-palo-alto-firewall-investigation.kql)

## Evidence

### Firewall Activity Overview

![Palo Alto Firewall Overview](screenshots/03-palo-alto-firewall-overview.png.png)

### Firewall Device Actions

![Palo Alto Device Actions](screenshots/03-palo-alto-firewall-device-actions.png.png)

## Findings

A KQL query summarized Palo Alto firewall activity by device action.

The investigation identified **125 denied connections**, **23 allowed connections**, and **1 firewall alert**. These results demonstrate how Microsoft Sentinel can be used to analyze firewall policy enforcement and identify network activity that may require additional investigation.

## Upcoming Investigation Steps

- Step 4 – Identity Investigation (Okta & Microsoft Entra ID)
- Step 5 – Windows Security Investigation
- Step 6 – Cross-Source Event Correlation
- Step 7 – Enterprise SOC Investigation Summary

---

## Repository Contents

| Folder | Description |
|---------|-------------|
| queries | KQL queries used during the investigation |
| screenshots | Evidence captured from Microsoft Sentinel |
| notes | Detailed investigation notes |
| README.md | Project documentation |

---

## Project Status

🚧 In Progress





