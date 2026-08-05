# Incident Investigation Configuration

## Overview

This document describes the Microsoft Sentinel incident investigation environment used during this implementation. The investigation was performed using the modern Microsoft Sentinel incident experience to analyze a real security incident and review the associated security evidence.

---

## Investigation Objectives

* Access Microsoft Sentinel incidents.
* Review incident information.
* Analyze associated entities.
* Review MITRE ATT&CK mappings.
* Understand the incident timeline.
* Prepare the incident for analyst investigation.

---

## Investigation Environment

The investigation was performed using the following Microsoft Sentinel components:

* Incidents
* Incident Overview
* Entities
* Incident Timeline
* MITRE ATT&CK Mapping
* Investigation Workspace

---

## Selected Incident

The following incident was selected for investigation.

| Property       | Value                                |
| -------------- | ------------------------------------ |
| Incident Title | Suspicious AWS CLI Command Execution |
| Severity       | Medium                               |
| Status         | New                                  |
| Owner          | Unassigned                           |
| Alert Product  | Microsoft Sentinel                   |

---

## Incident Description

Microsoft Sentinel generated an alert indicating potentially suspicious execution of AWS Command Line Interface (CLI) commands. The detection focuses on reconnaissance-related AWS CLI activity that may indicate an attacker gathering information about cloud resources before attempting additional actions.

---

## Entity Configuration

The investigation identified one associated entity.

| Entity Type | Entity |
| ----------- | ------ |
| Account     | mirage |

The account entity became the primary object of investigation during the incident analysis.

---

## MITRE ATT&CK Mapping

Microsoft Sentinel automatically mapped the incident to the following MITRE ATT&CK tactic.

| Tactic         |
| -------------- |
| Reconnaissance |

This mapping assists analysts in understanding the attack stage represented by the detected activity.

---

## Investigation Components Reviewed

During the investigation, the following Microsoft Sentinel components were reviewed:

* Incident Overview
* Incident Timeline
* Incident Description
* Related Entity
* MITRE ATT&CK Tactic
* Rule Information
* System Alert Information

---

## Configuration Result

The Microsoft Sentinel incident investigation environment successfully provided the information required to analyze the selected security incident. The incident data, associated entity, timeline, and MITRE ATT&CK mapping established a foundation for further investigation and response by the Security Operations Center (SOC).

