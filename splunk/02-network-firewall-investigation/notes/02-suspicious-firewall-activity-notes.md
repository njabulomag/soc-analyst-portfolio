# Suspicious Firewall Activity — Investigation Notes

## Objective

The objective of this investigation was to identify potentially suspicious network activity recorded by the firewall.

## Data Source

* Index: `main`
* Source: `firewall.csv`
* Log Type: Firewall / Network Traffic
* Firewall Category: `PaloAlto-Firewall`

## Investigation Focus

The investigation focused on firewall events where the traffic action was:

* `deny`
* `port_scan`

These event types were selected because they can indicate blocked connection attempts or network reconnaissance activity.

## SPL Query

```spl
index=main source="firewall.csv"
| eval f=split(_raw,",")
| eval action=mvindex(f,0), src_port=mvindex(f,1), src_ip=mvindex(f,2), dest_port=mvindex(f,3), traffic_action=mvindex(f,4), protocol=mvindex(f,6), severity=mvindex(f,7), category=mvindex(f,8), dest_ip=mvindex(f,9), dest_port2=mvindex(f,10), event_time=mvindex(f,11), user=mvindex(f,12)
| search traffic_action="deny" OR traffic_action="port_scan"
| stats count by traffic_action src_ip dest_ip dest_port protocol user
| sort - count
```

## Key Observations

The results identified multiple denied connections from external source IP addresses.

The investigation also identified `port_scan` activity involving external IP addresses and internal destination systems.

Examples of external source IP addresses observed include:

* `185.199.108.10`
* `45.77.21.19`
* `91.214.124.8`
* `203.0.113.50`

Internal destination addresses included systems in the `10.10.x.x` range.

The results also showed activity involving ports such as:

* `80` — HTTP
* `3389` — Remote Desktop Protocol (RDP)

## Security Relevance

Repeated denied connections may indicate unsuccessful access attempts.

`port_scan` events are particularly important because network scanning can be used during reconnaissance to identify open ports and available services.

Activity involving port `3389` should receive additional attention because RDP is commonly targeted during unauthorized access attempts.

## Recommended SOC Follow-Up

A SOC analyst should:

1. Investigate the source IP addresses in other security data sources.
2. Check whether the destination systems generated related Windows or endpoint alerts.
3. Review activity involving RDP port `3389`.
4. Determine whether the `port_scan` activity was expected.
5. Correlate the firewall events with endpoint, authentication, VPN, and proxy logs.
6. Escalate the investigation if the same source IP appears across multiple security sources.

## SOC Analyst Takeaway

Firewall logs provide valuable visibility into attempted and blocked network communications.

Filtering for denied traffic and port scanning can quickly highlight events that require further investigation and correlation with other SOC data sources.
