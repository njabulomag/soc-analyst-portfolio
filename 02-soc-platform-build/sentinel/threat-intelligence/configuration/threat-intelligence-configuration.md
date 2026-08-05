# Threat Intelligence Configuration

## Overview

This document describes the configuration of Microsoft Sentinel Threat Intelligence using the modern STIX 2.1 object model. The implementation establishes a centralized repository for Indicators of Compromise (IOCs) that can be used during threat detection, investigation, and incident response.

---

## Configuration Objectives

* Configure Microsoft Sentinel Threat Intelligence.
* Familiarize with the STIX 2.1 Threat Intelligence interface.
* Prepare Microsoft Sentinel for manual IOC management.
* Establish a Threat Intelligence repository.

---

## Configuration Steps

### Step 1 – Open Microsoft Sentinel

Navigate to the Microsoft Sentinel workspace and select **Threat Intelligence** from the navigation pane.

This workspace provides centralized management of Threat Intelligence objects.

---

### Step 2 – Review the Threat Intelligence Workspace

Review the available Threat Intelligence options including:

* Threat Intelligence objects
* Relationships
* Search
* Filtering
* Management options

This step provides an understanding of how Microsoft Sentinel stores and manages STIX Threat Intelligence.

---

### Step 3 – Create a New Threat Intelligence Object

Select **New → TI Object**.

Choose:

* **Object Type:** Indicator

This creates a new STIX 2.1 Indicator object that can represent an IP address, domain, file hash, or other observable.

---

### Step 4 – Configure Indicator Properties

During indicator creation the following properties were configured:

* Name
* Description
* Confidence Score
* Severity
* Valid Until
* Indicator Type
* Observable Type

These properties improve the quality and usefulness of Threat Intelligence data.

---

### Step 5 – Save the Indicator

After completing the required fields, save the Threat Intelligence object.

Microsoft Sentinel stores the object within the Threat Intelligence repository for future detection and investigation.

---

## Configuration Result

The Threat Intelligence workspace was successfully configured and prepared for manual Indicator of Compromise (IOC) management using the STIX 2.1 framework.

Subsequent implementation steps focused on creating and validating multiple IOC types.

