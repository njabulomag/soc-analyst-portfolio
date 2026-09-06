# Firewall Traffic Overview — Investigation Notes

## Objective

The objective of this investigation was to review firewall traffic and identify communication patterns between external source IP addresses and internal destination systems.

## Data Source

* Index: `main`
* Source: `firewall.csv`
* Log Type: Firewall / Network Traffic
* Firewall Category: PaloAlto-Firewall

## SPL Query

```spl
index=main source="firewall.csv"
| eval f=split(_raw,",")
| eval action=mvindex(f,0), src_port=mvindex(f,1), src_ip=mvindex(f,2), dest_port=mvindex(f,3), traffic_action=mvindex(f,4), protocol=mvindex(f,6), severity=mvindex(f,7), category=mvindex(f,8), dest_ip=mvindex(f,9), dest_port2=mvindex(f,10), event_time=mvindex(f,11), user=mvindex(f,12)
| stats count by traffic_action src_ip dest_ip protocol user
| sort - count
```

## Investigation Approach

The query separates the comma-separated firewall event data into individual fields using `split()` and `mvindex()`.

The investigation then groups events by:

* Traffic action
* Source IP address
* Destination IP address
* Protocol
* User

The results are sorted by event count to highlight the most frequently observed network activity.

## Key Observations

The results showed several different firewall traffic actions, including:

* `allow`
* `deny`
* `network_connection`
* `port_scan`

External IP addresses observed in the results included:

* `45.77.21.19`
* `203.0.113.50`
* `91.214.124.8`
* `185.199.108.10`

Internal destination addresses included systems such as:

* `10.10.10.15`
* `10.10.10.21`
* `10.10.30.18`

## Security Relevance

The presence of `deny` events and `port_scan` activity is relevant to SOC investigations because it may indicate reconnaissance or attempted network access.

The `network_connection` events should also be reviewed to determine whether the connections were expected or potentially suspicious.

Source IP addresses generating repeated or unusual activity should be investigated further using other available security logs.

## SOC Analyst Takeaway

A SOC analyst can use firewall logs to identify:

1. Repeated connections from external IP addresses.
2. Blocked or denied network traffic.
3. Potential port scanning activity.
4. Internal systems receiving external connections.
5. Users associated with network activity.

This investigation provides an initial network baseline and can be used as a starting point for deeper threat investigation.
