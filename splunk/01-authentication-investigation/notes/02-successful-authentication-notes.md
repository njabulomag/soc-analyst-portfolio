# Successful Authentication

## Objective

Identify successful Windows authentication events and summarize them by user, source IP address, device, and process.

## Data Source

* Index: `main`
* Source: `windows-security.csv`
* Event type: `4624_success`

## SPL Query

```spl
index=main source="windows-security.csv"
| search "4624_success"
| rex field=_raw "^[^,]*,(?<device>[^,]*),(?<src_ip>[^,]*),(?<event_id>[^,]*),(?<event_type>[^,]*),(?<field6>[^,]*),(?<process>[^,]*),(?<severity>[^,]*),(?<category>[^,]*),(?<dest_ip>[^,]*),(?<event_time>[^,]*),(?<user>[^,\r\n]*)"
| stats count by user src_ip device process
| sort - count
```

## Investigation Fields

The query extracts:

* `user`
* `src_ip`
* `device`
* `process`

The results are then grouped and counted to identify repeated successful authentication activity.

## Security Relevance

Successful authentication events are important because attackers who obtain valid credentials may use them to access systems without triggering a traditional failed-login pattern.

The source IP, device, user, and process provide useful context for determining whether authentication activity is legitimate.

## Analyst Takeaway

An SOC analyst should investigate authentication activity involving unusual source IP addresses, unexpected devices, privileged accounts, or suspicious processes.

Repeated successful authentication activity can also help identify accounts or systems that require further investigation.
