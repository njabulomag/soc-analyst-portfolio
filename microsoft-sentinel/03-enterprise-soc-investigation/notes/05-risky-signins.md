# Step 5 – Risky Sign-ins Investigation

## Objective

Investigate Microsoft Entra ID sign-in risk levels to determine whether any authentication events were classified as risky.

## Query Used

[05-risky-signins.kql](../queries/05-risky-signins.kql)

## Query

```kql
EntraIdSignInEvents
| summarize SignInCount = count() by RiskLevelAggregated
| order by SignInCount desc
```

## Query Explanation

This query groups Microsoft Entra ID sign-in events by their aggregated risk level.

- **EntraIdSignInEvents** selects authentication logs.
- **summarize** groups events by risk level.
- **count()** counts the number of sign-ins in each risk category.
- **order by** sorts the results from the highest count to the lowest.

## Findings

The investigation analyzed **3,925 sign-in events**.

| Risk Level | Sign-ins |
|-----------|---------:|
| 0 (No Risk) | 3925 |

All recorded sign-ins were classified as **No Risk**, indicating that Microsoft Entra ID did not identify suspicious authentication activity during the selected time period.

Although no risky sign-ins were detected, this investigation demonstrates how Microsoft Sentinel can be used to monitor identity risk and establish a security baseline.

## Skills Demonstrated

- Microsoft Sentinel
- Microsoft Entra ID
- Identity Protection
- Authentication Monitoring
- Kusto Query Language (KQL)
- SOC Investigation

## Key Learning

Monitoring sign-in risk helps SOC analysts quickly identify potentially compromised accounts and prioritize investigations. Even when no risky sign-ins are detected, documenting the results establishes a baseline for future comparisons.

## Evidence

Screenshot:

`05-risky-signins-overview.png`
