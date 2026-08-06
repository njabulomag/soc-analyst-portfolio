# Workbook Customization

## Overview

Microsoft Sentinel Workbooks allow Security Operations Center (SOC) analysts to customize dashboards by using parameters, filters, queries, and visualizations. Customization enables analysts to focus on specific security events, incidents, and operational metrics relevant to their investigations.

This document describes the workbook customization features reviewed during this implementation.

---

## Workbook Parameters

The **LabWorkbook** uses configurable parameters to filter dashboard data before queries are executed.

The following parameters were available:

| Parameter         | Purpose                                         |
| ----------------- | ----------------------------------------------- |
| Incident Severity | Filters incidents by severity level.            |
| Status            | Filters incidents by status.                    |
| Owner             | Filters incidents by assigned owner.            |
| Tags              | Filters incidents using assigned tags.          |
| Incident Number   | Displays a specific incident by its identifier. |

These parameters allow analysts to narrow the displayed data and focus on relevant incidents.

---

## Parameter Configuration

During validation, the following parameter values were configured:

| Parameter         | Selected Value |
| ----------------- | -------------- |
| Incident Severity | Medium, Low    |
| Status            | Active, New    |
| Tags              | All            |
| Incident Number   | Blank          |

After configuring these parameters, the workbook successfully displayed the dashboard.

---

## Workbook Customization Features

Microsoft Sentinel Workbooks support several customization capabilities, including:

* Interactive dashboard parameters.
* Dynamic filtering.
* Custom Kusto Query Language (KQL) queries.
* Tables and charts.
* Operational dashboards.
* Workspace monitoring.
* Log Analytics reporting.

These features enable analysts to tailor dashboards to operational and investigative requirements.

---

## Customization Validation

The customization process confirmed that:

* Workbook parameters could be configured.
* Parameter values controlled the displayed data.
* Dashboard queries executed successfully after required parameters were set.
* Interactive filtering improved the usability of the workbook.

---

## Operational Benefits

Workbook customization provides several advantages:

* Faster investigation workflows.
* Improved dashboard usability.
* Focused incident analysis.
* Flexible security monitoring.
* Better operational reporting.
* Enhanced visibility into Microsoft Sentinel data.

---

## Lessons Learned

During this implementation, the following observations were made:

* Some workbook queries require parameter values before execution.
* Proper parameter configuration is essential for dashboard functionality.
* Interactive filters simplify the analysis of security information.
* Microsoft Sentinel Workbooks can be adapted to different operational scenarios through parameter customization.

---

## Conclusion

The workbook customization process successfully demonstrated how Microsoft Sentinel dashboards can be configured using interactive parameters. By setting the required filters, the LabWorkbook loaded successfully and provided meaningful visualizations, confirming the flexibility and usefulness of workbook customization within a SOC environment.
