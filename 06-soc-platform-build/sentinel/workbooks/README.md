# Microsoft Sentinel Workbooks

## Overview

Microsoft Sentinel Workbooks provide interactive dashboards that help Security Operations Center (SOC) analysts visualize security data collected within Microsoft Sentinel. Workbooks combine charts, tables, metrics, and other visualizations to support monitoring, investigation, and operational reporting.

This guide documents the implementation and validation of Microsoft Sentinel Workbooks within the Sentinel lab environment.

## Objectives

* Review available Microsoft Sentinel workbooks.
* Explore workbook dashboards.
* Validate workbook functionality.
* Review workspace monitoring information.
* Document workbook implementation.

## Workbooks Reviewed

The following workbooks were available during this implementation:

* LabWorkbook
* Workspace & Lake Usage

## Folder Structure

```text
workbooks/
├── configuration/
├── customization/
├── validation/
├── notes/
└── screenshots/
```

## Screenshots

| Screenshot                                | Description                               |
| ----------------------------------------- | ----------------------------------------- |
| 01-workbooks-overview.png.png             | Available Microsoft Sentinel workbooks    |
| 02-labworkbook-dashboard.png.png          | LabWorkbook after parameter configuration |
| 03-workspace-lake-usage-dashboard.png.png | Workspace & Lake Usage workbook           |
| 04-workspace-summary.png.png              | Workspace summary dashboard               |

## Validation Summary

The implementation confirmed that Microsoft Sentinel Workbooks were successfully deployed and accessible. During testing, the LabWorkbook required parameter initialization before displaying data. After configuring the required parameters, the workbook loaded successfully. The Workspace & Lake Usage workbook also loaded successfully and provided operational visibility into the Sentinel workspace.

## Conclusion

Microsoft Sentinel Workbooks provide valuable visualization capabilities that assist SOC analysts with monitoring, operational awareness, and security investigations. Both available workbooks were successfully reviewed and validated during this implementation.

