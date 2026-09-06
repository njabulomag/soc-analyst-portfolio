# External IP Investigation — Investigation Notes

## Objective

The objective of this investigation was to identify external source IP addresses generating significant firewall activity and determine which internal systems they contacted.

## Data Source

* Index: `main`
* Source: `firewall.csv`
* Log Type: Firewall / Network Traffic
* Firewall Category: `PaloAlto-Firewall`

## SPL Query

```spl
index=main source="firewall.csv"
| eval f=split(_raw,",")
| eval action=mvindex(f,0), src_port=mvindex(f,1), src_ip=mvindex(f,2), dest_port=mvindex(f,3), traffic_action=mvindex(f,4), protocol=mvindex(f,6), severity=mvindex(f,7), category=mvindex(f,8), dest_ip=mvindex(f,9), dest_port2=mvindex(f,10), event_time=mvindex(f,11), user=mvindex(f,12)
| stats count dc(dest_ip) as unique_destinations values(dest_ip) as destination_ips values(traffic_action) as traffic_actions by src_ip
| sort - count
```

## Investigation Approach

The query groups firewall activity by external source IP address.

It calculates:

* Total number of events
* Number of unique internal destinations
* Internal destination IP addresses
* Types of firewall activity associated with each source IP

## Key Observations

Several external IP addresses generated repeated firewall activity against multiple internal destination systems.

The results showed traffic actions including:

* `allow`
* `deny`
* `network_connection`
* `port_scan`

Multiple source IP addresses contacted more than one internal destination.

## Security Relevance

An external IP communicating with multiple internal systems may require additional investigation, particularly when the same IP is associated with denied traffic or port scanning.

The combination of multiple destinations and different traffic actions can help a SOC analyst identify potentially suspicious network behaviour.

## Recommended SOC Follow-Up

1. Investigate high-volume external source IP addresses.
2. Check whether the same IP addresses appear in endpoint or authentication logs.
3. Review any `port_scan` activity associated with the source IP.
4. Investigate internal systems contacted by suspicious external sources.
5. Correlate the IP addresses with proxy, VPN, DNS, and endpoint data.
6. Determine whether the activity represents legitimate business traffic or potential reconnaissance.

## SOC Analyst Takeaway

Grouping firewall activity by source IP provides a quick way to identify external systems generating repeated or suspicious network activity.

This technique can help analysts prioritize external IP addresses for further investigation and correlation across multiple security data sources.
