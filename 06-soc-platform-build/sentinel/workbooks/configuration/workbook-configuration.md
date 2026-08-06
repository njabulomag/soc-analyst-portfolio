# Workbook Configuration

## Overview

Microsoft Sentinel Workbooks provide customizable dashboards that allow Security Operations Center (SOC) analysts to visualize security data collected across the Microsoft Sentinel environment.

This document describes the workbook configuration reviewed and validated during this implementation.

---

## Environment

| Setting            | Value                               |
| ------------------ | ----------------------------------- |
| Platform           | Microsoft Sentinel                  |
| Feature            | Workbooks                           |
| Workspace          | Sentinel Lab Workspace              |
| Workbooks Reviewed | LabWorkbook, Workspace & Lake Usage |

---

## LabWorkbook Configuration

The **LabWorkbook** was successfully opened from the Microsoft Sentinel Workbooks section.

The workbook contains configurable parameters that allow analysts to filter incident data before visualizations are generated.

### Configured Parameters

| Parameter         | Configuration   |
| ----------------- | --------------- |
| Incident Severity | Medium, Low     |
| Status            | Active, New     |
| Tags              | All             |
| Incident Number   | Blank (Default) |

After configuring the required parameters, the workbook successfully displayed dashboard information.

---

## Workspace & Lake Usage Configuration

The **Workspace & Lake Usage** workbook was opened and reviewed.

This workbook provides operational visibility into the Microsoft Sentinel workspace and Log Analytics environment by displaying usage information, workspace activity, and monitoring statistics.

No additional configuration was required before viewing the dashboard.

---

## Workbook Features

During the implementation, the following workbook capabilities were reviewed:

* Interactive dashboard visualizations.
* Configurable workbook parameters.
* Incident filtering.
* Workspace monitoring.
* Log Analytics usage reporting.
* Operational metrics.

---

## Configuration Validation

The workbook configuration was successfully validated.

The initial issue encountered with the LabWorkbook was resolved by configuring the required parameters, allowing workbook queries to execute successfully.

The Workspace & Lake Usage workbook loaded without configuration issues.

---

## Operational Benefits

Microsoft Sentinel Workbooks provide several operational benefits:

* Centralized security dashboards.
* Interactive filtering of security data.
* Improved operational visibility.
* Monitoring of Microsoft Sentinel workspace usage.
* Support for SOC investigations and reporting.

---

## Conclusion

The Microsoft Sentinel Workbook configuration was successfully completed. Both available workbooks were reviewed, required parameters were configured where necessary, and dashboard functionality was validated within the Microsoft Sentinel lab environment.
