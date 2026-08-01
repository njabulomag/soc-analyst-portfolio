# Step 3 – Explore the Threat Intelligence Schema

## Objective

Inspect the structure of the **ThreatIntelIndicators** table to identify the available fields before developing additional KQL queries.

## Query Used

[03-threat-intelligence-schema.kql](../queries/03-threat-intelligence-schema.kql)

## Findings

The `getschema` operator was used to display the structure of the **ThreatIntelIndicators** table.

The results showed 23 available columns, including:

- TimeGenerated
- Id
- IsActive
- ValidFrom
- ValidUntil
- Confidence
- Pattern
- ObservableKey
- ObservableValue
- Type

This step confirmed that the table schema in this environment differs slightly from the original lab documentation. Future queries will use the column names available in this environment.

## Skills Demonstrated

- Kusto Query Language (KQL)
- Schema Discovery
- Threat Intelligence
- Microsoft Defender XDR

## Evidence

Screenshot:

`03-threat-intelligence-schema.png`
