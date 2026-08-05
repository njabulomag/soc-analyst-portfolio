# Automation Configuration

## Overview

This document describes the configuration process used to create an Automation Rule in Microsoft Sentinel. The rule was designed to automatically respond to newly created high-severity incidents by applying predefined actions that support Security Operations Center (SOC) workflows.

---

## Configuration Objectives

* Configure a Microsoft Sentinel Automation Rule.
* Define the automation trigger.
* Configure incident conditions.
* Configure automated actions.
* Validate successful rule deployment.

---

## Step 1 – Create a New Automation Rule

A new Automation Rule was created from the Microsoft Sentinel **Automation** workspace.

**Rule Name**

```text
High Severity Incident Automation
```

The rule was enabled immediately after creation.

---

## Step 2 – Configure the Trigger

The trigger was configured as:

* **When incident is created**

This ensures the automation executes immediately whenever Microsoft Sentinel generates a new incident.

---

## Step 3 – Configure Conditions

The following condition was added:

| Property          | Operator | Value |
| ----------------- | -------- | ----- |
| Incident Severity | Equals   | High  |

This limits the automation to high-severity incidents only.

---

## Step 4 – Configure Actions

Two automated actions were configured.

### Action 1

* Add Tag
* Tag Value: **High-Priority**

### Action 2

* Add Comment

Comment added automatically:

> This incident was automatically tagged by the High Severity Incident Automation rule for analyst review.

---

## Step 5 – Review Configuration

Before deployment, the Automation Rule configuration was reviewed to verify:

* Rule name
* Trigger
* Conditions
* Actions
* Enabled status

The validation completed successfully.

---

## Step 6 – Deploy Automation Rule

The Automation Rule was created successfully and became available within the Microsoft Sentinel Automation workspace.

---

## Configuration Result

The completed Automation Rule automatically performs the following tasks whenever a new **High** severity incident is created:

* Applies the **High-Priority** tag.
* Adds a standardized analyst comment.
* Ensures consistent handling of high-priority incidents.

This implementation demonstrates how Microsoft Sentinel Automation Rules can standardize incident handling and improve SOC efficiency.
