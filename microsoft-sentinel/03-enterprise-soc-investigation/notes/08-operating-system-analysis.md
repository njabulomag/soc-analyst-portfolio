# Step 8 – Operating System Analysis

## Objective

Analyze Microsoft Entra ID authentication logs to identify the operating systems used during user sign-ins and establish a baseline of approved operating systems within the environment.

## Query Used

[08-operating-system-analysis.kql](../queries/08-operating-system-analysis.kql)

## Query

```kql
EntraIdSignInEvents
| summarize SignInCount = count() by OSPlatform
| order by SignInCount desc
```

## Query Explanation

This query summarizes authentication events by operating system.

- **EntraIdSignInEvents** selects Microsoft Entra ID authentication logs.
- **summarize** groups authentication events by operating system.
- **count()** calculates the number of sign-ins for each operating system.
- **order by SignInCount desc** sorts the results from the highest number of sign-ins to the lowest.

This enables analysts to understand which operating systems are commonly used within the environment.

## Findings

The investigation identified the following operating systems:

| Operating System | Sign-ins |
|-----------------|----------:|
| Windows 10 | 2653 |
| Windows | 1454 |

The authentication activity was entirely Windows-based.

Windows 10 generated the highest number of authentication events, while additional authentication events were recorded under the generic Windows platform.

No unexpected operating systems such as Linux, macOS, Android, or iOS were observed during the selected time period.

These results establish the operating system baseline for the environment.

## Skills Demonstrated

- Microsoft Sentinel
- Microsoft Entra ID
- Identity Monitoring
- Operating System Analysis
- Authentication Investigation
- Kusto Query Language (KQL)
- SOC Investigation

## Key Learning

Operating system analysis helps analysts establish a baseline of approved devices and detect unexpected platforms that could indicate unauthorized access or policy violations.

## Evidence

Screenshot:

`08-operating-system-analysis-overview.png`
