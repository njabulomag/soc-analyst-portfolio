# Step 1 – View Threat Intelligence Indicators

## Objective

Verify that the Microsoft Defender Threat Intelligence table is available and inspect any Indicators of Compromise (IOCs) stored in the environment.

## Query Used

[01-view-threat-intelligence-indicators.kql](../queries/01-view-threat-intelligence-indicators.kql)

## Findings

The query executed successfully against the **ThreatIntelIndicators** table.

No threat intelligence indicators were returned during the investigation, indicating that no IOCs were currently available in the lab environment.

Although no records were returned, this step confirmed that the table exists and can be queried successfully using Kusto Query Language (KQL).

## Skills Demonstrated

- Microsoft Defender Threat Intelligence
- Kusto Query Language (KQL)
- Threat Intelligence Investigation
- Microsoft Sentinel

## Evidence

Screenshot:

`01-threat-intelligence-indicators.png`
