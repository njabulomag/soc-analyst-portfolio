# Step 1 – Validate Connected Data Sources

## Objective

Verify that Microsoft Sentinel is successfully ingesting security telemetry from multiple enterprise security platforms before beginning the investigation.

## Query Used

[01-validate-data-sources.kql](../queries/01-validate-data-sources.kql)

## Query

```kql
union isfuzzy=true
(
    CrowdStrikeAlerts
    | summarize Records = count()
    | extend Source = "CrowdStrike Alerts"
),
(
    CommonSecurityLog
    | summarize Records = count()
    | extend Source = "Palo Alto Firewall"
),
(
    OktaV2_CL
    | summarize Records = count()
    | extend Source = "Okta"
),
(
    EntraIdSignInEvents
    | summarize Records = count()
    | extend Source = "Microsoft Entra ID"
),
(
    SecurityEvent
    | summarize Records = count()
    | extend Source = "Windows Security"
)
| project Source, Records
| order by Source asc
```

## Findings

The query confirmed that Microsoft Sentinel is receiving telemetry from multiple enterprise security products.

The available data sources included:

| Source | Records |
|---------|--------:|
| CrowdStrike Alerts | 53 |
| Microsoft Entra ID | 3,663 |
| Okta | 36 |
| Palo Alto Firewall | 149 |
| Windows Security | 23,864 |

These results confirm that the workspace is ingesting endpoint, firewall, identity, and operating system security events, providing sufficient telemetry for cross-source investigations.

## Skills Demonstrated

- Microsoft Sentinel
- Data Source Validation
- Kusto Query Language (KQL)
- Enterprise Security Monitoring
- SOC Investigation

## Evidence

Screenshot:

`01-validate-data-sources.png`
