# Endpoint Security Investigation

## Objective

Investigate endpoint security activity from CrowdStrike EDR logs and identify suspicious activity involving users, devices, processes, source IP addresses, and MITRE ATT&CK techniques.

## Data Source

* Index: `main`
* Source: `crowdstrike.csv`
* Data type: CrowdStrike Endpoint Detection and Response (EDR)

## SPL Query

```spl
index=main source="crowdstrike.csv"
| rex field=_raw "^[^,]*,(?<src_ip>[^,]*),(?<activity>[^,]*),(?<device>[^,]*),[^,]*,(?<process>[^,]*),(?<severity>[^,]*),(?<category>[^,]*),(?<dest_ip>[^,]*),(?<mitre_technique>[^,]*),(?<event_time>[^,]*),(?<user>[^,\r\n]*)"
| stats count by activity device process user src_ip mitre_technique
| sort - count
```

## Investigation Fields

The query extracts and groups the following fields:

* `activity` — type of endpoint activity
* `device` — affected endpoint
* `process` — process involved in the activity
* `user` — account associated with the activity
* `src_ip` — source IP address
* `mitre_technique` — associated MITRE ATT&CK technique
* `count` — number of matching events

## Observations

The investigation identified several types of endpoint activity, including:

* Network connections
* Credential access activity
* PowerShell activity
* Malware detection events

Processes observed included:

* `powershell.exe`
* `rundll32.exe`
* `winword.exe`
* `cmd.exe`

Multiple source IP addresses were associated with endpoint activity, including:

* `45.77.21.19`
* `91.214.124.8`
* `185.199.108.10`
* `203.0.113.50`

The results also showed activity associated with several user accounts and multiple Windows endpoints.

## Security Relevance

This investigation is useful for identifying potentially suspicious endpoint behavior by correlating:

`User → Device → Process → Source IP → Activity → MITRE ATT&CK Technique`

PowerShell, `rundll32.exe`, and Microsoft Word activity can be important during endpoint investigations because attackers may abuse legitimate Windows processes to execute commands or deliver malicious activity.

## Analyst Takeaway

An SOC analyst can use this type of query to quickly identify which users, devices, processes, and source IP addresses are associated with suspicious endpoint activity.

The grouped results provide a starting point for deeper investigation. High-frequency or unusual combinations should be investigated further using the original events and additional log sources.

## Evidence

Screenshot:

`03-endpoint-security-investigation-results.png`
