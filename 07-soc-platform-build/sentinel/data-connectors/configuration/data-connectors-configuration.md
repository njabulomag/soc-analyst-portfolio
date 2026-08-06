# Data Connectors Configuration

## Overview

Microsoft Sentinel Data Connectors enable security telemetry to be collected from Microsoft services, cloud platforms, and third-party security solutions. These connectors serve as the primary mechanism for ingesting security data into Microsoft Sentinel, allowing Security Operations Center (SOC) analysts to monitor, investigate, and respond to security events from a centralized platform.

This document describes the data connector configuration reviewed during this implementation.

---

## Environment

| Setting          | Value                  |
| ---------------- | ---------------------- |
| Platform         | Microsoft Sentinel     |
| Feature          | Data Connectors        |
| Environment      | Microsoft Sentinel Lab |
| Connector Status | Connected              |

---

## Connected Microsoft Data Connectors

The following Microsoft security products were connected to the Sentinel workspace during validation:

| Data Connector                                  | Purpose                                                               |
| ----------------------------------------------- | --------------------------------------------------------------------- |
| Microsoft Defender XDR                          | Centralized incident correlation across Microsoft Defender products.  |
| Microsoft Defender for Endpoint                 | Endpoint detection and response (EDR) telemetry from Windows devices. |
| Microsoft Defender for Identity                 | Identity-based threat detection for Active Directory environments.    |
| Microsoft Defender for Cloud Apps               | Monitoring of cloud applications and SaaS activity.                   |
| Microsoft Defender for Office 365 (Preview)     | Email and collaboration security events.                              |
| Microsoft 365 Insider Risk Management (Preview) | Insider risk detection and monitoring.                                |
| Microsoft Entra ID Protection                   | Identity protection alerts and risky sign-in information.             |
| Microsoft Defender for Cloud (Tenant-based)     | Cloud workload protection and cloud security posture monitoring.      |

---

## Connector Functionality

The configured connectors provide Microsoft Sentinel with security telemetry from multiple security domains, including:

* Endpoint security
* Identity protection
* Email security
* Cloud application monitoring
* Cloud workload protection
* Insider risk monitoring
* Cross-product incident correlation

This centralized collection enables Microsoft Sentinel to correlate alerts from multiple Microsoft security products.

---

## Configuration Validation

The Data Connectors page confirmed that all reviewed connectors were connected and available for data ingestion.

The connector configuration pages were successfully accessed to verify their availability within the Microsoft Sentinel workspace.

---

## Operational Benefits

Microsoft Sentinel Data Connectors provide several operational advantages:

* Centralized security telemetry collection.
* Integration across Microsoft security products.
* Improved incident correlation.
* Enhanced visibility across multiple security domains.
* Support for threat hunting, automation, analytics rules, and investigations.

---

## Conclusion

The Microsoft Sentinel Data Connector configuration was successfully reviewed and validated. The connected Microsoft security products provide comprehensive telemetry that supports detection, investigation, automation, and monitoring activities throughout the SOC lifecycle.
