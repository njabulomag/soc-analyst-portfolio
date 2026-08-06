# Microsoft Sentinel Workbooks

## Overview

Microsoft Sentinel Workbooks provide interactive dashboards that enable Security Operations Center (SOC) analysts to visualize security data collected within Microsoft Sentinel. Workbooks combine charts, tables, metrics, and visualizations to support security monitoring, incident investigations, and operational reporting.

This guide documents the implementation, validation, and review of Microsoft Sentinel Workbooks in the Microsoft Sentinel lab environment.

---

## Objectives

* Review available Microsoft Sentinel workbooks.
* Explore workbook dashboards.
* Validate workbook functionality.
* Review workspace monitoring information.
* Document workbook implementation.

---

## Workbooks Reviewed

The following workbooks were available during this implementation:

* **LabWorkbook**
* **Workspace & Lake Usage**

---

## Folder Structure

```text
workbooks/
├── configuration/
├── customization/
├── validation/
├── notes/
└── screenshots/
```

---

## Screenshots

### 1. Workbooks Overview

![Workbooks Overview](https://github.com/njabulomag/soc-analyst-portfolio/blob/main/06-soc-platform-build/sentinel/workbooks/screenshots/01-workbooks-overview.png.png)

Displays the **My Workbooks** page showing the workbooks available in the Microsoft Sentinel lab environment.

---

### 2. LabWorkbook Dashboard

![LabWorkbook Dashboard](https://github.com/njabulomag/soc-analyst-portfolio/blob/main/06-soc-platform-build/sentinel/workbooks/screenshots/02-labworkbook-dashboard.png.png)

Shows the **LabWorkbook** after configuring the required parameters (**Incident Severity** and **Status**) and successfully loading the dashboard.

---

### 3. Workspace & Lake Usage Dashboard

![Workspace & Lake Usage](https://github.com/njabulomag/soc-analyst-portfolio/blob/main/06-soc-platform-build/sentinel/workbooks/screenshots/03-workspace-lake-usage-dashboard.png.png)

Displays the **Workspace & Lake Usage** workbook used to monitor Microsoft Sentinel workspace activity and Log Analytics usage.

---

### 4. Workspace Summary

![Workspace Summary](https://github.com/njabulomag/soc-analyst-portfolio/blob/main/06-soc-platform-build/sentinel/workbooks/screenshots/04-workspace-summary.png.png)

Shows the workspace summary section containing monitoring information and workspace usage metrics.

---

## Validation Summary

The Microsoft Sentinel Workbooks implementation was successfully validated.

During testing, the **LabWorkbook** initially required parameter configuration before queries could execute successfully. After configuring the required **Incident Severity** and **Status** parameters, the workbook loaded correctly.

The **Workspace & Lake Usage** workbook loaded successfully and provided operational visibility into the Microsoft Sentinel workspace.

---

## Skills Demonstrated

* Microsoft Sentinel Workbooks
* Dashboard Validation
* Workbook Parameter Configuration
* Security Monitoring
* Microsoft Sentinel Visualization
* Operational Reporting
* Log Analytics Monitoring

---

## Conclusion

Microsoft Sentinel Workbooks provide valuable visualization capabilities that improve security monitoring and operational awareness. The implementation successfully validated both available workbooks, demonstrated workbook parameter configuration, and confirmed dashboard functionality within the Microsoft Sentinel lab environment.
