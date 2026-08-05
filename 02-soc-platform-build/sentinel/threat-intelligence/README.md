# Microsoft Sentinel – Threat Intelligence Implementation

## Project Overview

This implementation demonstrates how Microsoft Sentinel Threat Intelligence can be used to create, manage, and maintain Indicators of Compromise (IOCs) using the modern STIX 2.1 Threat Intelligence model. The objective was to configure Threat Intelligence within Microsoft Sentinel, manually create multiple IOC types, and validate that the indicators were successfully stored and available for future detection and investigation activities.

## Objectives

* Explore the Microsoft Sentinel Threat Intelligence workspace.
* Create Threat Intelligence (TI) objects using the STIX 2.1 model.
* Create and manage multiple Indicator of Compromise (IOC) types.
* Document the complete implementation process.
* Prepare Threat Intelligence data for future detection and investigation use.

## Technologies Used

* Microsoft Sentinel
* Microsoft Azure
* Log Analytics Workspace
* STIX 2.1 Threat Intelligence Objects
* Kusto Query Language (KQL)

## Implementation Summary

The implementation began by reviewing the Threat Intelligence workspace within Microsoft Sentinel. A new Threat Intelligence object was created using the current STIX 2.1 interface.

Three manual Indicators of Compromise were then created:

* Malicious IPv4 Address
* Malicious Domain
* Malicious SHA-256 File Hash

Each indicator included descriptive information, confidence scoring, expiration dates, and supporting metadata. After creation, the indicators were verified within the Threat Intelligence repository.

## Evidence

| Screenshot    | Description                              |
| ------------- | ---------------------------------------- |
| Screenshot 01 | Threat Intelligence Overview             |
| Screenshot 02 | New Threat Intelligence Object           |
| Screenshot 03 | Manual IPv4 Indicator                    |
| Screenshot 04 | Manual Domain Indicator                  |
| Screenshot 05 | Manual SHA-256 Indicator                 |
| Screenshot 06 | Threat Intelligence Indicator Repository |
| Screenshot 07 | Final Threat Intelligence Indicator List |

## Skills Demonstrated

* Microsoft Sentinel Threat Intelligence
* STIX 2.1 Indicator Management
* IOC Creation
* Threat Intelligence Administration
* Security Documentation
* KQL Validation
* SOC Documentation Best Practices

## Repository Structure

```text
threat-intelligence/
├── configuration/
├── indicators/
├── notes/
├── queries/
├── screenshots/
├── validation/
└── README.md
```

## Outcome

This implementation successfully demonstrated the creation and management of Threat Intelligence indicators using Microsoft Sentinel's modern STIX 2.1 framework. The completed implementation establishes a reusable Threat Intelligence foundation that can later be integrated with analytics rules, automation, investigations, and incident response workflows.

## Evidence

### Screenshot 01 – Threat Intelligence Overview

![Threat Intelligence Overview](screenshots/02-soc-platform-buildsentinelthreat-intelligencescreenshots01-threat-intelligence-overview.png.png)

### Screenshot 02 – New Threat Intelligence Object

![New Threat Intelligence Object](screenshots/02-soc-platform-buildsentinelthreat-intelligencescreenshots02-new-ti-object.png.png)

### Screenshot 03 – Manual IPv4 Indicator

![Manual IPv4 Indicator](screenshots/02-soc-platform-buildsentinelthreat-intelligencescreenshots03-manual-ip-indicator.png.png)

### Screenshot 04 – Manual Domain Indicator

![Manual Domain Indicator](screenshots/02-soc-platform-buildsentinelthreat-intelligencescreenshots04-manual-domain-indicator.png.png)

### Screenshot 05 – Manual SHA-256 Indicator

![Manual SHA-256 Indicator](screenshots/02-soc-platform-buildsentinelthreat-intelligencescreenshots05-manual-filehash-indicator.png.png)

### Screenshot 06 – Threat Intelligence Indicator List

![Threat Intelligence Indicator List](screenshots/02-soc-platform-buildsentinelthreat-intelligencescreenshots07-threat-intelligence-indicator-list.png.png)
