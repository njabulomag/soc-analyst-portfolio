# Incident Investigation Validation

## Overview

The purpose of this validation was to confirm that Microsoft Sentinel successfully generated a security incident and that the investigation features provided sufficient information for Security Operations Center (SOC) analysts to perform an initial investigation.

---

## Validation Objectives

The validation process confirmed that:

* Microsoft Sentinel successfully generated the incident.
* The incident appeared within the Incidents workspace.
* Incident metadata was available.
* Related entities were identified.
* MITRE ATT&CK mappings were provided.
* The incident timeline was available for review.

---

## Validation Process

### Step 1 – Verify Incident Availability

The Microsoft Sentinel **Incidents** page was reviewed.

The incident **Suspicious AWS CLI Command Execution** appeared successfully within the incident queue.

Verified information included:

* Incident Number
* Severity
* Status
* Alert Provider
* Created Time

---

### Step 2 – Verify Incident Details

The incident was opened to confirm that Microsoft Sentinel provided:

* Incident Description
* Severity
* Status
* Owner
* Timeline
* Rule Information

All information was successfully displayed.

---

### Step 3 – Verify Entity Mapping

The investigation identified one associated entity.

| Entity Type | Entity |
| ----------- | ------ |
| Account     | mirage |

Microsoft Sentinel successfully associated the account with the investigated incident.

---

### Step 4 – Verify MITRE ATT&CK Mapping

Microsoft Sentinel automatically classified the detected activity under the following MITRE ATT&CK tactic:

* Reconnaissance

This mapping assists analysts by identifying the attack stage associated with the alert.

---

### Step 5 – Verify Investigation Components

The following investigation components were available:

* Incident Overview
* Incident Timeline
* Entities
* System Alert ID
* Rule Information
* Investigation Workspace

These components provide analysts with the information required to begin a security investigation.

---

## Validation Results

The validation confirmed that:

* The incident was successfully generated.
* Microsoft Sentinel correctly displayed incident metadata.
* The associated account entity was available for investigation.
* MITRE ATT&CK mapping was automatically applied.
* The investigation interface provided sufficient information for initial incident analysis.

---

## Conclusion

The incident investigation implementation was successfully validated using a real Microsoft Sentinel security incident. The available incident information, entity mapping, timeline, and ATT&CK classification demonstrate how Microsoft Sentinel supports analysts during incident triage and investigation. This implementation provides a practical example of the investigation workflow used within a modern Security Operations Center.
