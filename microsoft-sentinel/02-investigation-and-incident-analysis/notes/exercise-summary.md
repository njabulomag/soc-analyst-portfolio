# Exercise 2 Summary – Microsoft Defender Threat Intelligence

## Overview

This project explored the Microsoft Defender Threat Intelligence capabilities available through Microsoft Defender XDR and Microsoft Sentinel.

Multiple Kusto Query Language (KQL) queries were executed to inspect the Threat Intelligence data, validate the availability of the ThreatIntelIndicators table, and understand its schema.

## Activities Performed

- Verified access to the ThreatIntelIndicators table.
- Counted available Threat Intelligence Indicators.
- Explored the table schema using the `getschema` operator.
- Reviewed indicator status using the `IsActive` and `Revoked` fields.
- Attempted to categorize indicators by type.
- Queried for active Threat Intelligence Indicators.

## Results

The Microsoft Defender environment contained no Threat Intelligence Indicators during the investigation period.

Although no threat intelligence data was available, every query executed successfully and confirmed that the ThreatIntelIndicators table was accessible and ready for future investigations.

## Skills Demonstrated

- Microsoft Defender XDR
- Microsoft Sentinel
- Kusto Query Language (KQL)
- Threat Intelligence Investigation
- Schema Discovery
- Security Data Analysis
- Technical Documentation

## Conclusion

This exercise demonstrated how to access and investigate Microsoft Defender Threat Intelligence data using KQL. While the lab environment did not contain active indicators, the investigation validated the available schema and confirmed the ability to perform future threat intelligence analysis when indicators are present.
