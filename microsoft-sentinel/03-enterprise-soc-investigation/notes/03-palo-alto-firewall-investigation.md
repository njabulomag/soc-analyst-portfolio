# Step 3 – Palo Alto Firewall Investigation

## Objective

Investigate Palo Alto firewall activity to understand how network traffic is being handled, identify blocked and allowed connections, and determine whether any firewall events require further investigation.

## Query Used

[03-palo-alto-firewall-investigation.kql](../queries/03-palo-alto-firewall-investigation.kql)

## Query

```kql
CommonSecurityLog
| summarize Events = count() by DeviceAction
| order by Events desc
```

## Query Explanation

This query summarizes firewall activity by the action taken on each network connection.

- **CommonSecurityLog** selects the Palo Alto firewall logs.
- **summarize** groups similar records together.
- **count()** counts how many events belong to each action.
- **by DeviceAction** groups the events by firewall action (Allow, Deny, Alert).
- **order by Events desc** sorts the results from the highest number of events to the lowest.

Rather than reviewing every firewall log individually, this query provides a high-level overview of firewall activity.

## Findings

The query returned the following results:

| Device Action | Events |
|--------------|-------:|
| Deny | 125 |
| Allow | 23 |
| Alert | 1 |

The firewall denied the majority of network connections, demonstrating that security policies were actively blocking unauthorized or suspicious traffic.

Twenty-three connections were successfully allowed based on the configured firewall policies.

One event generated a firewall alert. Although only a single alert was observed, it would normally be prioritized during an investigation because firewall alerts often indicate traffic that matched a security policy or threat signature.

This investigation demonstrates how Microsoft Sentinel can summarize network security events to help analysts quickly understand firewall activity and prioritize suspicious events for further analysis.

## Skills Demonstrated

- Microsoft Sentinel
- Palo Alto Firewall
- Network Security Monitoring
- Kusto Query Language (KQL)
- Security Event Analysis
- SOC Investigation

## Key Learning

This exercise introduced the **summarize** operator in KQL.

The `summarize` operator groups large volumes of log data into meaningful statistics, allowing analysts to identify trends and prioritize investigations without reviewing every individual event.

## Evidence

Screenshot:

`03-palo-alto-firewall-overview.png`
