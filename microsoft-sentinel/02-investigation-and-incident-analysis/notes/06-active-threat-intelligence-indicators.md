# Step 6 – Review Active Threat Intelligence Indicators

## Objective

Identify active Threat Intelligence Indicators stored in the Microsoft Defender Threat Intelligence table.

## Query Used

[06-active-threat-intelligence-indicators.kql](../queries/06-active-threat-intelligence-indicators.kql)

## Query

```kql
ThreatIntelIndicators
| where IsActive == true
| project
    TimeGenerated,
    Type,
    ObservableValue,
    Confidence,
    ValidUntil
| order by TimeGenerated desc
```

## Findings

A KQL query was executed to retrieve active Threat Intelligence Indicators.

The query completed successfully but returned no results because no active indicators were available in the lab environment during the selected time frame.

This exercise demonstrated how active indicators can be filtered and reviewed when threat intelligence data is present.

## Skills Demonstrated

- Microsoft Defender Threat Intelligence
- Kusto Query Language (KQL)
- Threat Hunting
- Security Data Analysis

## Evidence

Screenshot:

`06-active-threat-intelligence-indicators.png`
