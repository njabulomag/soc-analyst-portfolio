# Microsoft Sentinel Project 02 – Investigation and Incident Analysis

## Project Overview

This project documents the completion of **Exercise 2** from the Microsoft Sentinel Training Lab.

The purpose of this exercise is to investigate security incidents, correlate evidence from multiple data sources, and document the investigation process using Microsoft Sentinel and Microsoft Defender.

---

# Step 1 – View Threat Intelligence Indicators

## Query

[01-view-threat-intelligence-indicators.kql](queries/01-view-threat-intelligence-indicators.kql)

## Evidence

![Threat Intelligence Indicators](screenshots/01-threat-intelligence-indicators.png.png)

## Findings

A KQL query was executed against the **ThreatIntelIndicators** table to verify the availability of Threat Intelligence Indicators (IOCs).

The query completed successfully but returned no records, indicating that no threat intelligence indicators were currently present in the lab environment. This step confirmed that the table is available and ready for future threat intelligence investigations.

---

# Step 2 – Threat Intelligence Summary

## Query

[02-threat-intelligence-summary.kql](queries/02-threat-intelligence-summary.kql)

## Evidence

![Threat Intelligence Summary](screenshots/02-threat-intelligence-summary.png.png)

## Findings

A KQL count query was executed against the **ThreatIntelIndicators** table to determine whether any threat intelligence indicators were present.

The query completed successfully and returned a count of **0**, confirming that no indicators were available in the lab environment during this investigation. This verified that the table is accessible and ready for future threat intelligence data.
## Skills Demonstrated

- Microsoft Sentinel
- Microsoft Defender XDR
- Threat Investigation
- Incident Analysis
- Kusto Query Language (KQL)
- Event Correlation
- MITRE ATT&CK
- Security Operations (SOC)

---

## Project Structure

```
02-investigation-and-incident-analysis/

├── queries/
├── screenshots/
├── notes/
└── README.md
```
