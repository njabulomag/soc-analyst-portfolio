# Implementation Notes

## Overview

These notes document observations, challenges, lessons learned, and recommendations identified during the Microsoft Sentinel Threat Intelligence implementation.

---

## Implementation Summary

The implementation focused on configuring Microsoft Sentinel Threat Intelligence using the STIX 2.1 object model and manually creating Indicators of Compromise (IOCs). Three IOC types were successfully created and stored within the Threat Intelligence repository:

* IPv4 Address
* Domain Name
* SHA-256 File Hash

The implementation demonstrated the complete workflow for creating and managing Threat Intelligence objects in Microsoft Sentinel.

---

## Observations

Several differences were identified between current Microsoft Sentinel documentation and the live Microsoft Sentinel environment used during this project.

Examples included:

* The Threat Intelligence interface uses the modern STIX 2.1 object model.
* Confidence is represented as a numeric value (1–100) instead of Low, Medium, or High.
* Some KQL schema fields differ from older Microsoft documentation.
* Threat Intelligence ingestion into Log Analytics may not be immediate after creating indicators.

These observations highlight the importance of validating implementations against the current platform rather than relying solely on older documentation.

---

## Challenges

The following challenges were encountered during implementation:

* KQL queries returned different schemas than expected from older documentation.
* Some documented fields, such as `Pattern` and `ValidUntil`, were not available in the current environment.
* Newly created indicators were visible in the Threat Intelligence repository before they were consistently available through all KQL queries.

These issues were resolved by validating the current table schema and confirming indicator creation through the Microsoft Sentinel interface.

---

## Lessons Learned

This implementation reinforced several key lessons:

* Verify the current schema before developing KQL queries.
* Use meaningful names and descriptions for Indicators of Compromise.
* Apply consistent confidence scores and severity levels.
* Include expiration dates for indicators to support lifecycle management.
* Validate successful implementation using both the Microsoft Sentinel interface and KQL where applicable.

---

## Recommendations

For production environments, the following practices are recommended:

* Regularly review and update Threat Intelligence indicators.
* Remove expired or obsolete indicators.
* Validate new indicators before using them in analytics rules.
* Integrate Threat Intelligence with analytics rules, automation rules, and incident response workflows.
* Periodically review the Threat Intelligence repository to maintain data quality.

---

## Conclusion

The implementation successfully established a functional Threat Intelligence repository within Microsoft Sentinel using the STIX 2.1 framework. The documented process provides a repeatable approach for creating, managing, and validating Indicators of Compromise that can support future threat detection, investigations, and Security Operations Center (SOC) activities.

