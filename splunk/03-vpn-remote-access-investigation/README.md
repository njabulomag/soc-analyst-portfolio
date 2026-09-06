# Splunk Project 03 – VPN & Remote Access Investigation

## Overview

This project demonstrates a Security Operations Center (SOC) investigation of VPN and remote-access activity using Splunk.

The investigation focuses on identifying authentication failures, MFA failures, new-device activity, successful VPN logins, and source IP addresses generating high volumes of remote-access activity.

## Objectives

* Analyze VPN authentication activity.
* Identify VPN login and MFA failures.
* Investigate suspicious source IP addresses.
* Identify users and locations associated with VPN activity.
* Detect potentially suspicious remote-access behavior.
* Demonstrate practical Splunk SPL investigation techniques.

## Data Source

* **Splunk Index:** `main`
* **Source:** `vpn.csv`
* **Log Type:** VPN / Remote Access

---

# Investigation 01 – VPN Authentication Overview

### Objective

Establish an overview of VPN authentication activity and identify the different types of remote-access events occurring in the environment.

### Query

```spl
index=main source="vpn.csv"
| eval f=split(_raw,",")
| eval action=mvindex(f,0), src_ip=mvindex(f,1), user=mvindex(f,2), device=mvindex(f,3), result=mvindex(f,4), protocol=mvindex(f,5), severity=mvindex(f,6), category=mvindex(f,7), dest_ip=mvindex(f,8), event_time=mvindex(f,9)
| stats count by action src_ip user device result
| sort - count
```

### Screenshot

![VPN Authentication Overview](screenshots/01-vpn-authentication-overview-results.png)

### Key Observations

The investigation identified multiple types of VPN activity, including:

* VPN login successes
* VPN login failures
* MFA failures
* New-device activity

Activity was associated with multiple users, source IP addresses, devices, and geographic locations.

### SOC Relevance

Authentication activity provides an initial view of remote-access behavior and can help analysts identify accounts or systems requiring further investigation.

---

# Investigation 02 – VPN Login Failures

### Objective

Identify failed VPN authentication and MFA events that could indicate attempted unauthorized access.

### Query

```spl
index=main source="vpn.csv"
| eval f=split(_raw,",")
| eval action=mvindex(f,0), src_ip=mvindex(f,1), event_type=mvindex(f,2), location=mvindex(f,3), empty_field=mvindex(f,4), port=mvindex(f,5), severity=mvindex(f,6), category=mvindex(f,7), dest_ip=mvindex(f,8), event_time=mvindex(f,9), user=mvindex(f,10), device=mvindex(f,11)
| search event_type="VPNLoginFailure" OR event_type="MFAFailure"
| stats count by event_type src_ip user location device
| sort - count
```

### Screenshot

![VPN Login Failures](screenshots/02-vpn-login-failures-results.png)

### Key Observations

The query identified VPN login failures and MFA failures involving multiple source IP addresses and user accounts.

Observed activity included users such as:

* `admin`
* `alice.smith`
* `john.doe`
* `mike.wilson`
* `sarah.jones`
* `svc-backup`

Multiple geographic locations were also observed, including Johannesburg, Cape Town, London, and New York.

### SOC Relevance

Repeated authentication or MFA failures can be indicators of:

* Password spraying
* Brute-force attempts
* Compromised credentials
* MFA abuse
* Unauthorized remote access attempts

These events should be correlated with successful authentication activity to determine whether an attacker eventually gained access.

---

# Investigation 03 – VPN Source IP Investigation

### Objective

Identify source IP addresses generating large volumes of VPN activity and determine how many users, locations, and event types are associated with each source.

### Query

```spl
index=main source="vpn.csv"
| eval f=split(_raw,",")
| eval action=mvindex(f,0), src_ip=mvindex(f,1), event_type=mvindex(f,2), location=mvindex(f,3), empty_field=mvindex(f,4), port=mvindex(f,5), severity=mvindex(f,6), category=mvindex(f,7), dest_ip=mvindex(f,8), event_time=mvindex(f,9), user=mvindex(f,10), device=mvindex(f,11)
| stats count dc(user) as unique_users dc(location) as unique_locations values(event_type) as event_types values(user) as users values(location) as locations by src_ip
| sort - count
```

### Screenshot

![VPN Source IP Investigation](screenshots/03-vpn-source-ip-investigation-results.png)

### Key Findings

Four source IP addresses generated significant VPN activity:

| Source IP        | Events | Unique Users | Unique Locations |
| ---------------- | -----: | -----------: | ---------------: |
| `45.77.21.19`    |    260 |            6 |                4 |
| `203.0.113.50`   |    260 |            6 |                4 |
| `185.199.108.10` |    254 |            6 |                4 |
| `91.214.124.8`   |    244 |            6 |                4 |

Each source IP was associated with six users and four geographic locations.

The observed event types included VPN login failures, MFA failures, new-device events, and successful VPN logins.

### SOC Relevance

A source IP generating high volumes of VPN activity across multiple accounts and geographic locations warrants additional investigation.

This behavior may be associated with:

* Credential compromise
* Password spraying
* MFA abuse
* Unauthorized remote access
* Compromised VPN credentials
* Attempts to access multiple user accounts

The combination of failed and successful authentication activity is particularly important because it may indicate that an authentication attempt eventually succeeded.

---

# Recommended SOC Investigation

If this activity were observed in a production SOC environment, the analyst should:

1. Investigate the reputation of the source IP addresses.
2. Review the affected user accounts.
3. Identify successful logins following authentication failures.
4. Review MFA activity.
5. Investigate new-device events.
6. Correlate VPN activity with firewall logs.
7. Correlate activity with endpoint security logs.
8. Verify whether the geographic locations are expected.
9. Check for impossible-travel or unusual-location behavior.
10. Escalate confirmed suspicious activity according to the incident-response process.

---

# Skills Demonstrated

* Splunk SPL
* VPN log analysis
* Authentication investigation
* MFA investigation
* Source IP analysis
* User behavior analysis
* Geographic activity analysis
* Security event correlation
* Suspicious remote-access detection
* SOC investigation methodology

---

# Project Outcome

This project demonstrates the ability to investigate remote-access activity from multiple perspectives.

The investigation progressed from a general overview of VPN authentication activity to targeted analysis of failed authentication attempts and finally to source-IP-based investigation.

These techniques are commonly used by SOC analysts when investigating potentially compromised accounts and suspicious remote-access activity.

