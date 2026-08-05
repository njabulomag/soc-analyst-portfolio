# Indicator Management

## Overview

Effective Threat Intelligence depends not only on creating Indicators of Compromise (IOCs), but also on maintaining their accuracy and relevance throughout their lifecycle. Microsoft Sentinel provides centralized management of Threat Intelligence indicators using the STIX 2.1 framework.

---

## Indicator Lifecycle

Each indicator follows a lifecycle that includes:

1. Creation
2. Validation
3. Deployment
4. Monitoring
5. Updating
6. Expiration
7. Removal (if no longer relevant)

Maintaining this lifecycle helps ensure that outdated or inaccurate indicators do not affect security operations.

---

## Confidence Score

The Confidence Score indicates the reliability of an indicator.

For this implementation:

* Confidence Score: **90**

A high confidence score indicates that the indicator is considered reliable and suitable for security monitoring and investigation.

---

## Threat Severity

Each indicator was assigned a severity level of **High**.

High-severity indicators help analysts prioritize investigations and focus on threats that present a greater security risk.

---

## Expiration Management

Each indicator was configured with a future expiration date.

Expiration dates help ensure that stale or outdated indicators are reviewed and removed when they are no longer useful.

---

## Indicator Types

The following IOC types were implemented:

* IPv4 Address
* Domain Name
* SHA-256 File Hash

These indicator types represent common observables used during threat hunting, malware analysis, and incident response.

---

## Operational Benefits

Centralized indicator management provides several advantages:

* Improved threat visibility
* Consistent IOC management
* Faster threat investigations
* Better incident response
* Reusable threat intelligence
* Improved SOC efficiency

---

## Best Practices

During this implementation the following practices were followed:

* Created meaningful indicator names.
* Added descriptive metadata.
* Assigned high-confidence scores.
* Applied appropriate severity levels.
* Configured expiration dates.
* Validated successful creation within Microsoft Sentinel.

These practices improve the quality and usability of Threat Intelligence across the Security Operations Center (SOC).

---

## Outcome

The indicators created during this implementation are centrally managed within Microsoft Sentinel and are ready to support future detection rules, threat hunting activities, investigations, automation workflows, and incident response processes.

