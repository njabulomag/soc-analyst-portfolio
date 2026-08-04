# Microsoft Sentinel – Analytics Rules

## Business Objective

The objective of this implementation was to configure, validate, and document Microsoft Sentinel Analytics Rules used to detect suspicious security activity across the monitored environment.

The implementation demonstrates the ability to deploy detection logic, validate security telemetry, and generate Microsoft Sentinel incidents for Security Operations Center (SOC) investigations.

---

# Technologies

- Microsoft Sentinel
- Microsoft Azure
- Kusto Query Language (KQL)
- Windows Security Events
- MITRE ATT&CK Framework

---

# Data Sources

- SecurityEvent
- AWS CloudTrail
- Azure Activity
- Office Activity
- CommonSecurityLog
- CrowdStrike
- Okta

---

# Implementation Summary

During this implementation the existing Microsoft Sentinel analytics rules were reviewed and validated.

A custom Scheduled Analytics Rule was designed to detect repeated Windows failed logon events using Windows Security Event ID 4625.

The detection logic identifies accounts generating multiple failed authentication attempts and generates Microsoft Sentinel alerts for analyst investigation.

---

# Custom Detection

**Rule Name**

Multiple Failed Windows Logons

**Data Source**

SecurityEvent

**Severity**

Medium

**MITRE ATT&CK**

Credential Access (TA0006)

Brute Force (T1110)

---

# Validation

The custom detection was validated using production telemetry available within the Microsoft Sentinel workspace.

Validation confirmed that the detection successfully identified multiple Windows accounts generating repeated failed authentication attempts.

The Analytics Rule was successfully deployed and enabled.

---

# Evidence

The following evidence was collected during implementation:

- Analytics Rules Overview
- Built-in Analytics Rule Configuration
- Custom KQL Validation
- Analytics Rule Configuration
- Rule Logic Configuration
- Incident Configuration
- Automation Configuration
- Rule Deployment

Supporting screenshots are available in the **screenshots** directory.

---

# Skills Demonstrated

- Microsoft Sentinel
- Detection Engineering
- Kusto Query Language (KQL)
- Analytics Rule Development
- Security Monitoring
- Windows Event Analysis
- MITRE ATT&CK Mapping
- SOC Detection Validation

---

# Repository Structure

```text
analytics-rules/
│
├── configuration/
├── detections/
├── notes/
├── queries/
├── screenshots/
├── validation/
└── README.md
```

---

# Outcome

The Microsoft Sentinel Analytics Rules implementation provides validated detection capability for Windows authentication attacks while establishing a repeatable process for future detection engineering activities across the SOC Platform Build.


# Evidence

## Figure 1 - Analytics Rules Overview

![Analytics Rules Overview](screenshots/01-analytics-overview.png.png)

The Microsoft Sentinel Analytics Rules page showing active detection rules, rule severity, MITRE ATT&CK mappings, and rule status.

---

## Figure 2 - Built-in Analytics Rule

![Built-in Analytics Rule](screenshots/02-built-in-analytics-rule.png.pg)

Configuration of the built-in **NRT Security Event Log Cleared** rule demonstrating Microsoft's detection engineering approach.

---

## Figure 3 - Custom KQL Validation

![Custom KQL Validation](screenshots/03-custom-kql-validation.png.png)

Validation of the custom KQL query showing repeated Windows failed logon attempts detected from the **SecurityEvent** table.

---

## Figure 4 - Custom Rule General Configuration

![Rule General Configuration](screenshots/04-custom-rule-general.png.png)

General configuration of the custom Analytics Rule including name, severity, description, and MITRE ATT&CK mapping.

---

## Figure 5 - Rule Logic

![Rule Logic](screenshots/05-custom-rule-logic.png.png)

Detection logic configured for the custom Scheduled Analytics Rule.

---

## Figure 6 - Incident Settings

![Incident Settings](screenshots/06-incident-settings.png.png)

Incident creation configuration for the Analytics Rule.

---

## Figure 7 - Automation

![Automation](screenshots/07-automation-page.png.png)

Automation configuration showing no playbooks attached during the initial implementation.

---

## Figure 8 - Review and Create

![Review and Create](screenshots/08-review-and-create.png.png)

Final review prior to deploying the custom Analytics Rule.

---

## Figure 9 - Analytics Rule Created

![Analytics Rule Created](screenshots/09-custom-rule-created.png.png)

Confirmation that the custom Analytics Rule was successfully deployed and enabled.
