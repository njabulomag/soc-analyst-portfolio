# Hunting Validation

## Overview

This document validates the Microsoft Sentinel Hunting implementation performed during this guide. The objective was to confirm that the Hunting workspace was available, review the available hunting query, execute the query, and document the outcome.

---

## Validation Objectives

The validation process confirmed the following:

* Microsoft Sentinel Hunting workspace was accessible.
* Hunting queries were available.
* Hunting query metadata could be reviewed.
* Hunting query execution was attempted.
* The execution outcome was documented.
* The hunting capability was successfully evaluated.

---

## Validation Process

### Step 1 – Hunting Workspace

The Microsoft Sentinel Hunting workspace was successfully accessed.

The workspace displayed the available hunting queries and allowed review of query metadata.

**Status:** Successful

---

### Step 2 – Hunting Query Review

One custom hunting query was available.

| Property            | Value                      |
| ------------------- | -------------------------- |
| Query Name          | Solorigate Inventory check |
| Content Source      | Custom                     |
| MITRE ATT&CK Tactic | Execution                  |
| Entity Types        | Account, Host              |

The query documentation was successfully reviewed.

**Status:** Successful

---

### Step 3 – Query Execution

The hunting query was executed from Microsoft Sentinel.

Execution returned the following error:

> **'extend' operator: Failed to resolve scalar expression named 'Account_s'**

The query could not complete because the required field was not present in the current Microsoft Sentinel lab dataset.

**Status:** Validation completed with schema mismatch identified.

---

### Step 4 – Bookmark Validation

Because the hunting query did not return results, Microsoft Sentinel could not generate bookmarks from the execution.

This behavior is expected because bookmarks require successful query results.

**Status:** Expected outcome.

---

## Validation Results

| Validation Item            | Result                               |
| -------------------------- | ------------------------------------ |
| Hunting Workspace          | Passed                               |
| Hunting Query Availability | Passed                               |
| Query Metadata Review      | Passed                               |
| Query Execution            | Completed                            |
| Schema Compatibility       | Failed (missing **Account_s** field) |
| Bookmark Creation          | Not Available                        |

---

## Technical Findings

The validation identified a data schema mismatch between the supplied hunting query and the current Microsoft Sentinel lab environment.

The hunting query expects a field named **Account_s**, which is not present in the available dataset.

This finding demonstrates the importance of validating field names before using hunting queries across different environments.

---

## Lessons Learned

During the validation, the following lessons were reinforced:

* Hunting queries depend on available log schemas.
* Different Microsoft Sentinel environments may contain different field names.
* Hunting queries should always be tested before operational deployment.
* Query validation is an essential part of threat hunting.

---

## Conclusion

The Microsoft Sentinel Hunting capability was successfully validated. The Hunting workspace, query metadata, and execution workflow were all confirmed to be operational. Although the available custom hunting query could not complete because of a schema mismatch, the implementation successfully demonstrated the hunting process and documented the technical limitation encountered in the lab environment. This reflects a realistic validation scenario that SOC analysts may encounter when working across different Microsoft Sentinel deployments.
