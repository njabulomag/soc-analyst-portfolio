# VPN Login Failures — Investigation Notes

## Objective

The objective of this investigation was to identify failed VPN authentication and MFA events that may require further investigation.

## Data Source

* Index: `main`
* Source: `vpn.csv`
* Log Type: VPN / Remote Access

## SPL Query

```spl
index=main source="vpn.csv"
| eval f=split(_raw,",")
| eval action=mvindex(f,0), src_ip=mvindex(f,1), event_type=mvindex(f,2), location=mvindex(f,3), empty_field=mvindex(f,4), port=mvindex(f,5), severity=mvindex(f,6), category=mvindex(f,7), dest_ip=mvindex(f,8), event_time=mvindex(f,9), user=mvindex(f,10), device=mvindex(f,11)
| search event_type="VPNLoginFailure" OR event_type="MFAFailure"
| stats count by event_type src_ip user location device
| sort - count
```

## Investigation Approach

The query filters the VPN dataset for failed VPN login and MFA authentication events.

The results are grouped by:

* Event type
* Source IP
* User
* Location
* Device

This helps identify repeated authentication failures and potentially suspicious access patterns.

## Key Observations

The investigation identified multiple `VPNLoginFailure` and `MFAFailure` events.

Several source IP addresses appeared repeatedly across the results, including:

* `185.199.108.10`
* `203.0.113.50`
* `45.77.21.19`
* `91.214.124.8`

The activity was associated with multiple users and locations.

Locations observed included Johannesburg, Cape Town, London, and New York.

## Security Relevance

Repeated VPN login failures may indicate:

* Incorrect credentials
* Password-guessing attempts
* Unauthorized access attempts
* Account targeting

MFA failures are also important because they may indicate an authentication attempt that did not successfully complete multi-factor authentication.

## Recommended SOC Follow-Up

1. Identify source IPs generating the highest number of failures.
2. Determine whether multiple users are being targeted by the same IP.
3. Correlate failed logins with successful VPN logins.
4. Investigate unusual geographic locations.
5. Check the same IP addresses in firewall and endpoint logs.
6. Review whether the affected users reported legitimate VPN access attempts.
7. Escalate activity showing repeated failures followed by successful authentication.

## SOC Analyst Takeaway

Failed VPN and MFA events are valuable indicators during remote-access investigations.

A SOC analyst should correlate repeated authentication failures with successful access, source IP reputation, user activity, device information, and geographic context before determining whether the activity is malicious.
