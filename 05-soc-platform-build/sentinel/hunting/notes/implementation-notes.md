# Implementation Notes

## Overview

These implementation notes summarize the Microsoft Sentinel Hunting exercise completed during this guide. The implementation focused on reviewing the Hunting workspace, analyzing an available custom hunting query, validating its execution, and documenting the observed results.

---

## Implementation Summary

The Microsoft Sentinel Hunting workspace was successfully accessed and reviewed.

The implementation included:

* Reviewing the Hunting workspace.
* Examining available hunting queries.
* Reviewing hunting query metadata.
* Executing a custom hunting query.
* Validating the execution results.
* Documenting the observed behavior.

One custom hunting query, **Solorigate Inventory check**, was available within the lab environment.

---

## Observations

Several important observations were made during this implementation:

* Microsoft Sentinel Hunting provides a dedicated workspace for proactive threat hunting.
* Hunting queries are written using Kusto Query Language (KQL).
* Queries include MITRE ATT&CK mappings and supported entity types.
* Hunting queries rely on the structure of available log data.
* Schema differences between environments can prevent a hunting query from executing successfully.

---

## Technical Findings

The **Solorigate Inventory check** query was executed as part of the validation process.

Execution returned the following error:

> **'extend' operator: Failed to resolve scalar expression named 'Account_s'**

This indicates that the query expected a field named **Account_s**, which was not present in the current Microsoft Sentinel lab dataset.

The issue represents a schema mismatch rather than a Microsoft Sentinel platform failure.

---

## Lessons Learned

This implementation reinforced several important Security Operations Center (SOC) concepts:

* Threat hunting depends on high-quality log collection.
* Hunting queries must be compatible with the available data schema.
* Analysts should validate field names before using custom hunting queries.
* Hunting activities often require adapting queries to different environments.
* Careful documentation of validation results supports troubleshooting and future improvements.

---

## Best Practices

The following best practices were identified during this implementation:

* Review hunting query documentation before execution.
* Verify required tables and fields exist.
* Test hunting queries in the target environment.
* Document any schema differences.
* Update custom queries when log schemas change.
* Maintain version control for custom hunting queries.

---

## Recommendations

Future improvements include:

* Updating the query to match the current lab schema.
* Validating additional hunting queries if they become available.
* Expanding hunting activities to include Microsoft Defender, Azure Activity, Microsoft Entra ID, and AWS log sources.
* Creating custom hunting queries tailored to the available datasets.
* Using successful hunting results to create bookmarks and support incident investigations.

---

## Conclusion

The Microsoft Sentinel Hunting implementation successfully demonstrated the proactive hunting workflow used by Security Operations Center analysts. Although the available custom query encountered a schema mismatch during execution, the implementation validated the Hunting workspace, reviewed query metadata, confirmed query execution, and documented the technical limitation. This exercise reflects a realistic operational scenario in which analysts must evaluate, troubleshoot, and adapt hunting queries to match the data available within a specific Microsoft Sentinel environment.

