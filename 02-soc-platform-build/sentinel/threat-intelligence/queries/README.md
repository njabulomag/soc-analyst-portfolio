# Threat Intelligence KQL Queries

## Overview

The following Kusto Query Language (KQL) queries were used during the Microsoft Sentinel Threat Intelligence implementation. These queries were executed to validate the Threat Intelligence environment and verify indicator ingestion.

---

# Query 1 – Display Threat Intelligence Indicators

```kusto
ThreatIntelligenceIndicator
| sort by TimeGenerated desc
```

### Purpose

Displays all Threat Intelligence indicators ordered by creation time.

### Result

Successfully returned the manually created Threat Intelligence indicators.

---

# Query 2 – Display Threat Intelligence Table Schema

```kusto
ThreatIntelligenceIndicator
| getschema
```

### Purpose

Displays the available columns within the Threat Intelligence table.

### Result

Used to identify the current Microsoft Sentinel schema and confirm available fields such as:

* TimeGenerated
* Description
* ConfidenceScore
* IndicatorId
* ThreatType
* ExpirationDateTime
* ThreatSeverity
* Active
* Tags

---

# Query 3 – Display Recent Threat Intelligence Records

```kusto
ThreatIntelligenceIndicator
| take 10
```

### Purpose

Displays the most recent Threat Intelligence records stored in Microsoft Sentinel.

### Result

Used during implementation to verify that Threat Intelligence records were available for analysis.

---

## Notes

During the implementation, several Microsoft Sentinel environments exposed different Threat Intelligence schemas. The queries documented in this guide were validated against the implementation environment used for this project.

Schema differences between Microsoft Sentinel versions may affect the availability of certain columns. Using `getschema` is recommended to verify the current table structure before developing additional Threat Intelligence queries.

