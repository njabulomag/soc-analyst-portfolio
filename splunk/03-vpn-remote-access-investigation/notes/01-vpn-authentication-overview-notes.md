# VPN Authentication Overview — Investigation Notes

## Objective

The objective of this investigation was to review VPN authentication activity and identify successful logins, failed login attempts, MFA failures, and new-device activity.

## Data Source

* Index: `main`
* Source: `vpn.csv`
* Log Type: VPN / Remote Access

## SPL Query

```spl
index=main source="vpn.csv"
| eval f=split(_raw,",")
| eval action=mvindex(f,0), src_ip=mvindex(f,1), user=mvindex(f,2), device=mvindex(f,3), result=mvindex(f,4), protocol=mvindex(f,5), severity=mvindex(f,6), category=mvindex(f,7), dest_ip=mvindex(f,8), event_time=mvindex(f,9)
| stats count by action src_ip user device result
| sort - count
```

## Investigation Approach

The query separates the VPN log fields and groups the events by:

* Action
* Source IP address
* User
* Device
* Result

The results were sorted by event count to highlight repeated VPN activity.

## Key Observations

The investigation identified several VPN-related events, including:

* `VPNLoginSuccess`
* `VPNLoginFailure`
* `MFAFailure`
* `NewDevice`

The results also showed activity associated with multiple external IP addresses and locations.

Locations observed included:

* Johannesburg
* Cape Town
* London
* New York

## Security Relevance

Repeated VPN login failures may indicate password-guessing or unauthorized access attempts.

MFA failures are important because they may indicate attempts to authenticate without successfully completing multi-factor authentication.

New-device events should also be reviewed to determine whether the device was expected and authorized for the user.

Successful VPN logins should be correlated with preceding failed login or MFA events to determine whether suspicious activity resulted in successful access.

## Recommended SOC Follow-Up

1. Investigate repeated VPN login failures.
2. Review MFA failures associated with the same source IP.
3. Check whether successful logins occurred after multiple failures.
4. Verify whether new devices are known and authorized.
5. Correlate VPN activity with Entra ID authentication logs.
6. Correlate suspicious activity with endpoint and firewall logs.
7. Investigate unusual geographic locations or impossible travel patterns.

## SOC Analyst Takeaway

VPN logs provide important visibility into remote access activity.

A SOC analyst should pay particular attention to repeated failures, MFA failures, new-device events, and successful authentication following suspicious activity.
