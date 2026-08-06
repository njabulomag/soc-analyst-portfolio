# Hunting Configuration

## Overview

This document describes the Microsoft Sentinel Hunting configuration reviewed during this implementation. Hunting enables Security Operations Center (SOC) analysts to proactively search for suspicious activity using Kusto Query Language (KQL) without relying solely on automatically generated alerts or incidents.

---

## Configuration Objectives

The objectives of this implementation were to:

* Review the Microsoft Sentinel Hunting workspace.
* Examine available hunting queries.
* Understand hunting query metadata.
* Validate hunting query execution.
* Confirm hunting capability within the Microsoft Sentinel environment.

---

## Hunting Workspace

The Microsoft Sentinel Hunting workspace provides a centralized location for managing hunting queries.

The workspace allows analysts to:

* Browse available hunting queries.
* Search for specific hunting queries.
* Filter hunting queries.
* Review MITRE ATT&CK mappings.
* Examine supported entity types.
* Execute hunting queries.

During this implementation, the Hunting workspace was successfully accessed and reviewed.

---

## Hunting Query Reviewed

One custom hunting query was available within the Microsoft Sentinel workspace.

| Property            | Value                      |
| ------------------- | -------------------------- |
| Query Name          | Solorigate Inventory check |
| Content Source      | Custom                     |
| Entity Types        | Account, Host              |
| MITRE ATT&CK Tactic | Execution                  |

The query is designed to identify indicators associated with the SolarWinds (Solorigate) compromise by searching collected security logs.

---

## Query Structure

The hunting query is written using Kusto Query Language (KQL).

The query includes:

* Variable declaration.
* Time filtering.
* Event filtering.
* Sysmon event collection.
* Security Event collection.
* Data transformation.

These components allow Microsoft Sentinel to search for activity associated with known attack techniques.

---

## Query Execution

The hunting query was executed as part of the validation process.

Microsoft Sentinel returned the following error:

> **'extend' operator: Failed to resolve scalar expression named 'Account_s'**

This indicates that the current Microsoft Sentinel lab environment does not contain the field expected by the hunting query.

The error represents a data schema mismatch rather than a configuration failure.

---

## Configuration Validation

The implementation successfully confirmed that:

* Microsoft Sentinel Hunting is enabled.
* The Hunting workspace is operational.
* Hunting queries are available.
* Query metadata is accessible.
* Query execution is supported.
* Schema differences can affect hunting query execution.

---

## Operational Benefits

Microsoft Sentinel Hunting provides several advantages for SOC analysts:

* Proactive threat hunting.
* Investigation of suspicious activity.
* Detection of threats not covered by analytics rules.
* Flexible KQL-based investigations.
* Integration with MITRE ATT&CK tactics.
* Reusable hunting queries for ongoing security monitoring.

---

## Conclusion

The Microsoft Sentinel Hunting workspace was successfully reviewed and validated. Although the available custom hunting query encountered a schema mismatch during execution, the implementation confirmed that the hunting capability is properly configured and available for proactive threat investigations within the Microsoft Sentinel environment.
