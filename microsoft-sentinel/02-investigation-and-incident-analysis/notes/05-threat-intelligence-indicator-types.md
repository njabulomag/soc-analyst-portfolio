# Step 5 – Review Threat Intelligence Indicator Types

## Objective

Determine whether any Threat Intelligence Indicators are available and identify their types.

## Query Used

[05-threat-intelligence-indicator-types.kql](../queries/05-threat-intelligence-indicator-types.kql)

## Query

```kql
ThreatIntelIndicators
| summarize Count = count() by Type
| order by Count desc
```

## Findings

A KQL query was executed to group Threat Intelligence Indicators by their **Type**.

The query executed successfully but returned **no results**, indicating that no threat intelligence indicators were present in the lab environment during the selected time frame.

Although no indicator types were identified, this exercise demonstrated how to summarize and categorize indicators when threat intelligence data is available.

## Skills Demonstrated

- Microsoft Defender Threat Intelligence
- Kusto Query Language (KQL)
- Data Summarization
- Threat Intelligence Analysis

## Evidence

Screenshot:

`05-threat-intelligence-indicator-types.png`
