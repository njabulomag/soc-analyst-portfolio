# Hunting Bookmarks

## Overview

Microsoft Sentinel Bookmarks allow analysts to save important findings discovered during threat hunting. Bookmarks preserve evidence that can later be referenced during incident investigations, threat hunting activities, or security reporting.

---

## Objectives

The objectives of this implementation were to:

* Understand the purpose of Microsoft Sentinel Bookmarks.
* Determine whether hunting results could be bookmarked.
* Document the validation outcome.

---

## What Are Bookmarks?

Bookmarks provide analysts with a method for preserving important investigation findings.

Common bookmark use cases include:

* Suspicious user activity
* Malicious IP addresses
* Suspicious host activity
* Threat hunting evidence
* Indicators of compromise (IOCs)
* Investigation notes

Bookmarks help analysts return to important findings without rerunning complex hunting queries.

---

## Hunting Query Validation

The **Solorigate Inventory check** hunting query was executed during this implementation.

Execution returned the following error:

> **'extend' operator: Failed to resolve scalar expression named 'Account_s'**

Because the query did not complete successfully, no hunting results were produced.

---

## Bookmark Validation

Since the hunting query returned no results, a bookmark could not be created.

This is expected behavior because Microsoft Sentinel only allows bookmarks to be created from successful hunting results or log query results.

---

## Operational Workflow

A typical Microsoft Sentinel hunting workflow is:

1. Execute a hunting query.
2. Review the returned results.
3. Identify suspicious activity.
4. Create a bookmark for relevant findings.
5. Use the bookmark during investigations or incident response.

In this lab environment, the workflow stopped at the query validation stage due to the schema mismatch.

---

## Lessons Learned

This implementation demonstrated several important concepts:

* Bookmarks depend on successful hunting results.
* Hunting queries should be validated before investigations begin.
* Data schema differences can prevent query execution.
* Analysts should resolve query issues before attempting to bookmark findings.

---

## Conclusion

Although no bookmark was created during this implementation, the exercise successfully demonstrated the role of bookmarks within Microsoft Sentinel and highlighted their importance in preserving evidence during successful threat hunting investigations. The observed schema mismatch prevented result generation, making bookmark creation unavailable in the current lab environment.
