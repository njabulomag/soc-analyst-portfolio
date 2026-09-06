# Authentication Overview

## Objective

Review Windows Security authentication activity to understand which users, devices, source IP addresses, and processes are involved in authentication events.

## Data Source

* Index: `main`
* Source: `windows-security.csv`
* Log type: Windows Security

## Investigation

The investigation focuses on authentication-related Windows Security events and groups activity by important fields to identify patterns.

The analysis helps an SOC analyst understand:

* Which users are authenticating
* Which devices are involved
* Which source IP addresses are being used
* Which processes are associated with authentication activity
* How frequently authentication activity occurs

## Security Relevance

Authentication logs are important for detecting suspicious access, unusual login patterns, compromised accounts, and potentially unauthorized access to systems.

## Analyst Takeaway

An SOC analyst should compare authentication activity against the expected user, device, source IP, and process.

Unusual combinations or unexpectedly high authentication activity should be investigated further.
