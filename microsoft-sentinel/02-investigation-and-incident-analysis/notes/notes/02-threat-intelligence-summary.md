# Step 2 – Threat Intelligence Summary

## Objective

Determine whether any Threat Intelligence Indicators (IOCs) are currently stored in the Microsoft Defender Threat Intelligence table.

## Query Used

[02-threat-intelligence-summary.kql](../queries/02-threat-intelligence-summary.kql)

## Findings

A count query was executed against the **ThreatIntelIndicators** table.

The query completed successfully and returned a count of **0**, indicating that no threat intelligence indicators were present in the lab environment at the time of the investigation.

This confirms that the table is accessible and ready to store or query threat intelligence indicators when they become available.

## Skills Demonstrated

- Microsoft Defender Threat Intelligence
- Kusto Query Language (KQL)
- Threat Intelligence Investigation
- Data Validation

## Evidence

Screenshot:

`02-threat-intelligence-summary.png`
