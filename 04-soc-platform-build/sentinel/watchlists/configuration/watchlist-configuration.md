# Watchlist Configuration

## Overview

This document describes the Microsoft Sentinel Watchlist configuration reviewed during this implementation. Watchlists provide additional context that can be referenced by Kusto Query Language (KQL), Analytics Rules, Automation Rules, Hunting Queries, and Incident Investigations.

---

## Configuration Objectives

* Review existing Microsoft Sentinel Watchlists.
* Validate watchlist metadata.
* Confirm watchlist data sources.
* Verify Log Analytics integration.
* Confirm watchlist availability for investigations.

---

## Available Watchlists

Three watchlists were available within the Microsoft Sentinel workspace.

| Watchlist       | Purpose                                                               |
| --------------- | --------------------------------------------------------------------- |
| VIPUsers        | Stores privileged or high-value user accounts.                        |
| HighValueAssets | Stores important systems and business-critical assets.                |
| KnownBadIPs     | Stores known malicious IP addresses for threat intelligence matching. |

---

## KnownBadIPs Configuration

The **KnownBadIPs** watchlist was reviewed in detail.

| Property    | Value                                                                                          |
| ----------- | ---------------------------------------------------------------------------------------------- |
| Name        | KnownBadIPs                                                                                    |
| Source      | known_bad_ips.csv                                                                              |
| Provider    | Microsoft Sentinel                                                                             |
| Description | Known malicious IP addresses used in the Lab attack scenario for threat intelligence matching. |

The watchlist imports data from a CSV file and makes it available through Microsoft Sentinel for security investigations.

---

## Watchlist Source

The watchlists were configured using CSV files.

Examples include:

* vip_users.csv
* high_value_assets.csv
* known_bad_ips.csv

CSV-based watchlists allow organizations to maintain external data that can be referenced during investigations and threat hunting activities.

---

## Log Analytics Integration

Microsoft Sentinel automatically exposes watchlists through the `_GetWatchlist()` function.

The following queries were successfully reviewed:

```kusto
_GetWatchlist('KnownBadIPs')
```

```kusto
_GetWatchlist('VIPUsers')
```

```kusto
_GetWatchlist('HighValueAssets')
```

These queries provide direct access to watchlist contents from Log Analytics.

---

## Operational Benefits

Microsoft Sentinel Watchlists provide several operational advantages:

* Centralized reference data for investigations.
* Improved threat hunting capabilities.
* Faster analyst decision-making.
* Integration with Analytics Rules.
* Integration with Automation Rules.
* Support for incident enrichment.
* Consistent reference data across SOC workflows.

---

## Configuration Result

The Microsoft Sentinel workspace successfully provided three operational watchlists that can be queried from Log Analytics using KQL. The implementation confirmed that watchlists are correctly configured and available for use throughout Microsoft Sentinel, supporting investigations, analytics, automation, and threat hunting activities.

