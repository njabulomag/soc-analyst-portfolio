# VPN Remote Access Investigation Notes

## Investigation Overview

This investigation analyzed VPN and remote access events from `vpn.csv` using Splunk. The objective was to identify authentication activity, failed VPN logins, MFA failures, suspicious source IP addresses, affected users, and geographic access patterns.

The investigation results were used to create the **VPN & Remote Access Monitoring** dashboard.

---

## Data Source

* **Index:** `main`
* **Source:** `vpn.csv`
* **Time Range:** All time
* **Analysis Platform:** Splunk

The dataset contained VPN events including source IP addresses, event types, locations, destination devices, users, and timestamps.

---

# Investigation Findings

## 1. VPN Activity Over Time

A time-based visualization was created to monitor VPN activity across the available dataset.

This visualization helps SOC analysts identify unusual spikes in VPN activity and investigate periods with abnormal authentication behavior.

**Dashboard Panel:** VPN Activity Over Time

---

## 2. Authentication Success vs Failure

The investigation identified the following VPN authentication events:

| Event Type      | Count |
| --------------- | ----: |
| VPNLoginFailure |   228 |
| VPNLoginSuccess |   218 |

The number of failed VPN logins was slightly higher than successful logins.

This could indicate repeated authentication failures and should be monitored for possible password attacks, credential stuffing, or unauthorized access attempts.

**Dashboard Panel:** Authentication Success vs Failure

---

## 3. Top VPN Source IPs

The investigation identified multiple external source IP addresses generating VPN activity.

The most active source IP addresses included:

* `203.0.113.50`
* `185.199.108.10`
* `91.214.124.8`
* `45.77.21.19`

These IP addresses should be monitored to identify unusual activity patterns or repeated authentication attempts.

**Dashboard Panel:** Top VPN Source IPs

---

## 4. Top VPN Targeted Users

VPN activity was distributed across several users and service accounts.

The most active accounts included:

* `mike.wilson`
* `svc-backup`
* `sarah.jones`
* `admin`
* `john.doe`
* `alice.smith`

Service accounts and administrative accounts should receive additional monitoring because they may have elevated privileges or access to important systems.

**Dashboard Panel:** Top VPN Targeted Users

---

## 5. MFA Failures

The investigation identified:

**278 MFA failures**

Repeated MFA failures may indicate:

* Incorrect authentication attempts
* Credential attacks
* MFA fatigue attempts
* Unauthorized access attempts

MFA failures should be investigated when they occur repeatedly for the same user or source IP address.

**Dashboard Panel:** MFA Failures

---

## 6. VPN Login Failures by Source IP

The following source IP addresses generated failed VPN login attempts:

| Source IP      | Failed VPN Logins |
| -------------- | ----------------: |
| 185.199.108.10 |                76 |
| 45.77.21.19    |                60 |
| 203.0.113.50   |                48 |
| 91.214.124.8   |                44 |

The source IP address `185.199.108.10` generated the highest number of failed VPN login attempts.

This source IP should be prioritized during investigation because repeated authentication failures may indicate a password spraying or credential attack.

**Dashboard Panel:** VPN Login Failures by Source IP

---

## 7. MFA Failures by User

The MFA failure investigation identified the following affected users:

| User        | MFA Failures |
| ----------- | -----------: |
| svc-backup  |           62 |
| john.doe    |           46 |
| admin       |           44 |
| alice.smith |           42 |
| mike.wilson |           42 |
| sarah.jones |           42 |

The `svc-backup` account generated the highest number of MFA failures.

Service accounts experiencing authentication failures should be investigated to determine whether the activity is caused by configuration issues, expired credentials, automation failures, or unauthorized access attempts.

**Dashboard Panel:** MFA Failures by User

---

## 8. VPN Activity by Location

VPN activity was distributed across four locations:

| Location     | Events |
| ------------ | -----: |
| Cape Town    |    252 |
| New York     |    252 |
| Johannesburg |    248 |
| London       |    248 |

The activity distribution was relatively even across the locations.

SOC analysts should investigate unexpected geographic access, especially when the same user appears to authenticate from multiple geographically distant locations within a short period.

**Dashboard Panel:** VPN Activity by Location

---

# SOC Investigation Assessment

The VPN dataset contained several indicators that would require further investigation in a real SOC environment:

* High numbers of VPN authentication failures
* 278 MFA failures
* Repeated failed login attempts from the same source IP addresses
* Multiple users affected by MFA failures
* Activity involving administrative and service accounts
* VPN activity originating from multiple geographic locations

The highest-priority investigation areas would be repeated failures from `185.199.108.10` and repeated MFA failures involving the `svc-backup` account.

---

# Recommended SOC Actions

1. Investigate repeated VPN login failures from high-volume source IP addresses.
2. Review authentication activity associated with `185.199.108.10`.
3. Investigate the `svc-backup` account for repeated MFA failures.
4. Monitor administrative accounts such as `admin` for unusual VPN activity.
5. Correlate failed VPN logins with successful authentication events.
6. Investigate users authenticating from geographically distant locations.
7. Consider creating Splunk detection rules for repeated VPN failures and excessive MFA failures.

---

# Dashboard Summary

The completed Splunk dashboard contains eight SOC monitoring panels:

1. VPN Activity Over Time
2. Authentication Success vs Failure
3. Top VPN Source IPs
4. Top VPN Targeted Users
5. MFA Failures
6. VPN Login Failures by Source IP
7. MFA Failures by User
8. VPN Activity by Location

The dashboard provides a central view of VPN authentication activity and helps SOC analysts quickly identify suspicious remote access patterns.
