# Step 4 – Threat Intelligence Status

## Objective

Review the current status of Threat Intelligence Indicators stored in the Microsoft Defender Threat Intelligence table.

## Query Used

[04-threat-intelligence-status.kql](../queries/04-threat-intelligence-status.kql)

## Query

```kql
ThreatIntelIndicators
| summarize
    TotalIndicators = count(),
    ActiveIndicators = countif(IsActive == true),
    RevokedIndicators = countif(Revoked == true)
```

## Findings

A summary query was executed against the **ThreatIntelIndicators** table to determine the current status of threat intelligence indicators.

The query returned:

- Total Indicators: **0**
- Active Indicators: **0**
- Revoked Indicators: **0**

This confirms that the Threat Intelligence table is operational but currently contains no active or revoked indicators in the lab environment.

## Skills Demonstrated

- Microsoft Defender Threat Intelligence
- Kusto Query Language (KQL)
- Threat Intelligence Validation
- Security Data Analysis

## Evidence

Screenshot:

`04-threat-intelligence-status.png`
