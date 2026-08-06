# Data Connector Inventory

## Overview

This inventory documents the Microsoft data connectors that were connected to the Microsoft Sentinel workspace during the implementation of this guide. These connectors provide the security telemetry that powers analytics rules, incidents, hunting queries, workbooks, automation rules, watchlists, and investigations throughout the SOC environment.

---

## Connected Data Connectors

### Microsoft Defender XDR

**Status:** Connected

**Purpose**

Microsoft Defender XDR centralizes alerts and incidents from multiple Microsoft Defender security products, allowing Microsoft Sentinel to correlate activity across endpoint, identity, email, and cloud environments.

**Security Domain**

* Extended Detection and Response (XDR)

---

### Microsoft Defender for Endpoint

**Status:** Connected

**Purpose**

Provides endpoint detection and response (EDR) telemetry from managed Windows devices, including endpoint alerts, device events, and security incidents.

**Security Domain**

* Endpoint Security

---

### Microsoft Defender for Identity

**Status:** Connected

**Purpose**

Provides identity-based threat detection for Active Directory environments, including suspicious authentication activity and identity-related attacks.

**Security Domain**

* Identity Protection

---

### Microsoft Defender for Cloud Apps

**Status:** Connected

**Purpose**

Collects cloud application activity and SaaS security events, helping analysts detect risky user behavior and cloud-based threats.

**Security Domain**

* Cloud Application Security

---

### Microsoft Defender for Office 365 (Preview)

**Status:** Connected

**Purpose**

Provides security telemetry related to Microsoft 365 email, collaboration services, phishing attacks, and malicious attachments.

**Security Domain**

* Email Security

---

### Microsoft 365 Insider Risk Management (Preview)

**Status:** Connected

**Purpose**

Supports insider risk investigations by monitoring activities that may indicate data misuse or policy violations.

**Security Domain**

* Insider Risk

---

### Microsoft Entra ID Protection

**Status:** Connected

**Purpose**

Provides identity protection alerts, risky sign-ins, and user risk detections from Microsoft Entra ID.

**Security Domain**

* Identity Security

---

### Microsoft Defender for Cloud (Tenant-based)

**Status:** Connected

**Purpose**

Collects cloud security posture information, recommendations, alerts, and workload protection events from Microsoft Defender for Cloud.

**Security Domain**

* Cloud Security

---

## Summary

| Category                   | Connected |
| -------------------------- | --------: |
| Microsoft Defender XDR     |         ✓ |
| Endpoint Security          |         ✓ |
| Identity Security          |         ✓ |
| Cloud Security             |         ✓ |
| Cloud Application Security |         ✓ |
| Email Security             |         ✓ |
| Insider Risk               |         ✓ |

---

## Operational Importance

The connected Microsoft data connectors provide the telemetry required for:

* Analytics Rules
* Incident Creation
* Incident Investigation
* Threat Hunting
* Watchlists
* Automation Rules
* Workbooks
* Security Monitoring
* Security Reporting

These connectors form the foundation of the Microsoft Sentinel Security Operations Center by supplying the security events that enable detection and response activities.

---

## Conclusion

The Microsoft Sentinel workspace contained multiple connected Microsoft security products covering endpoint, identity, cloud, email, insider risk, and extended detection and response capabilities. Together, these connectors provide comprehensive telemetry that supports the complete SOC workflow implemented throughout this portfolio.
