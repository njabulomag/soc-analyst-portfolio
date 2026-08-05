# Threat Intelligence Validation

## Overview

Validation is an essential step in any Threat Intelligence implementation. The purpose of this validation was to confirm that manually created Indicators of Compromise (IOCs) were successfully stored within Microsoft Sentinel and available for future security operations.

---

# Validation Objectives

The validation process focused on confirming that:

* Microsoft Sentinel accepted manually created Threat Intelligence objects.
* The created indicators appeared within the Threat Intelligence repository.
* The indicators contained the expected metadata.
* Threat Intelligence records were available for future detection and investigation workflows.

---

# Validation Process

## Step 1 – Indicator Creation

Three Indicators of Compromise were successfully created using the STIX 2.1 Threat Intelligence interface.

Created indicators included:

* Malicious IPv4 Address
* Malicious Domain
* Malicious SHA-256 File Hash

Microsoft Sentinel confirmed successful creation of each Threat Intelligence object.

---

## Step 2 – Repository Verification

The Threat Intelligence workspace was reviewed to verify that the newly created indicators appeared within the repository.

The repository displayed the manually created indicators, confirming that Microsoft Sentinel successfully stored the Threat Intelligence objects.

---

## Step 3 – KQL Validation

Threat Intelligence validation queries were executed within Microsoft Sentinel Logs.

The following queries were used during validation:

```kusto id="hlnnho"
ThreatIntelligenceIndicator
| sort by TimeGenerated desc
```

```kusto id="t37f8v"
ThreatIntelligenceIndicator
| getschema
```

The schema query confirmed the available fields within the Threat Intelligence table, including:

* IndicatorId
* Description
* ConfidenceScore
* ThreatType
* ExpirationDateTime
* ThreatSeverity
* Active

---

# Validation Results

The implementation successfully demonstrated that:

* Microsoft Sentinel accepted all manually created indicators.
* Threat Intelligence objects were stored within the Threat Intelligence repository.
* Indicator metadata was successfully retained.
* The Threat Intelligence environment was correctly configured for future operational use.

---

# Challenges Encountered

During implementation, it was observed that KQL results did not immediately return the newly created indicators in every query. This behavior is consistent with Microsoft Sentinel environments where Threat Intelligence ingestion into Log Analytics may not occur instantly.

The successful appearance of the indicators within the Threat Intelligence repository confirmed that the implementation had completed successfully.

---

# Conclusion

The Threat Intelligence implementation was successfully validated through the Microsoft Sentinel interface and supporting KQL queries. The environment is now prepared to support future analytics rules, threat hunting activities, incident investigations, automation workflows, and incident response operations using the created Indicators of Compromise.

