# Step 4 – Microsoft Entra ID Application Sign-in Overview

## Objective

Analyze Microsoft Entra ID sign-in activity to identify which cloud applications are accessed most frequently and establish a baseline of normal authentication activity.

## Query Used

[04-identity-application-overview.kql](../queries/04-identity-application-overview.kql)

## Query

```kql
EntraIdSignInEvents
| summarize SignInCount = count() by Application
| order by SignInCount desc
```

## Query Explanation

This query summarizes Microsoft Entra ID sign-in events by application.

- **EntraIdSignInEvents** selects authentication logs from Microsoft Entra ID.
- **summarize** groups sign-in events by application.
- **count()** calculates the total number of sign-ins for each application.
- **order by SignInCount desc** sorts the results from the highest number of sign-ins to the lowest.

Rather than reviewing thousands of individual authentication events, this query provides a high-level overview of application usage across the environment.

## Findings

The investigation analyzed **3,903 authentication events**.

The most frequently accessed applications included:

| Application | Sign-ins |
|------------|---------:|
| Microsoft 365 Security | 2363 |
| Microsoft Defender | 764 |
| Windows Defender | 481 |
| Microsoft Threat Protection | 59 |
| Microsoft Exchange | 58 |
| Azure Portal | 58 |
| Security Copilot API | 50 |
| Microsoft Cloud App Security | 25 |
| Microsoft Azure Storage | 13 |
| ADIbizaUX | 13 |

The results establish a baseline of normal authentication activity within the environment.

Applications such as **Microsoft 365 Security**, **Microsoft Defender**, and **Windows Defender** generated the highest number of authentication events, reflecting normal usage of Microsoft's security services.

Administrative services such as **Azure Portal** and **Microsoft Exchange** should be monitored closely because unauthorized access to these applications could indicate account compromise or privilege misuse.

## Skills Demonstrated

- Microsoft Sentinel
- Microsoft Entra ID
- Identity Monitoring
- Authentication Analysis
- Cloud Security
- Kusto Query Language (KQL)
- SOC Investigation

## Key Learning

Security analysts use authentication logs to establish a baseline of normal user activity.

Understanding which applications are commonly accessed makes it easier to detect unusual authentication behavior, unauthorized access attempts, and compromised accounts.

## Evidence

### Screenshot 1

`04-entra-id-application-query.png`

### Screenshot 2

`04-entra-id-application-results.png`
