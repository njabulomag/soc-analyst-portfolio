# Step 4 – Investigate Blocked Firewall Traffic

## Objective

Identify the source IP addresses responsible for the highest number of blocked firewall connections.

## Query Used

[04-blocked-firewall-traffic.kql](../queries/04-blocked-firewall-traffic.kql)

## Key Findings

The analysis identified one source IP responsible for all blocked firewall activity.

| Source IP | Blocked Connections | Distinct Targeted Ports |
|-----------|--------------------:|------------------------:|
| 10.0.1.50 | 125 | 124 |

The source IP attempted connections to **124 different destination ports**, which is consistent with broad reconnaissance or port-scanning behavior. This activity should be investigated further to determine whether it is expected administrative activity or potentially malicious behavior.

## Evidence

Screenshot:

`04-blocked-firewall-traffic.png`
