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
