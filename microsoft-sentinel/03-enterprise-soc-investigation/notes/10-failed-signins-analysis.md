# Step 10 – Failed Authentication Analysis

## Objective

Analyze Microsoft Entra ID authentication failures to identify common sign-in errors and determine whether they indicate suspicious activity or normal operational events.

## Query Used

[10-failed-signins-analysis.kql](../queries/10-failed-signins-analysis.kql)

## Query

```kql
EntraIdSignInEvents
| summarize FailedSignIns = count() by ErrorCode
| where ErrorCode != 0
| order by FailedSignIns desc
```

## Query Explanation

This query summarizes authentication failures by Azure/Entra ID error code.

- **EntraIdSignInEvents** selects authentication logs.
- **summarize** groups events by error code.
- **count()** counts the number of failed sign-ins.
- **where ErrorCode != 0** filters out successful sign-ins.
- **order by FailedSignIns desc** sorts the results from the highest number of failures to the lowest.

This enables analysts to quickly identify the most common authentication failures and determine whether they require investigation.

## Findings

The investigation identified the following failed authentication events:

| Error Code | Failed Sign-ins |
|------------|----------------:|
| 70008 | 3 |
| 50011 | 1 |

A total of **4 failed authentication events** were recorded.

Error **70008** was the most common and is typically associated with expired or inactive refresh tokens. This generally represents normal session expiration rather than malicious activity.

Error **50011** occurred once and usually indicates an application configuration issue involving a redirect URI mismatch.

No evidence of password spraying, brute-force attacks, or widespread authentication failures was identified during this investigation.

## Skills Demonstrated

- Microsoft Sentinel
- Microsoft Entra ID
- Authentication Monitoring
- Identity Security
- Kusto Query Language (KQL)
- SOC Investigation

## Key Learning

Authentication failures should always be investigated in context. Error codes provide valuable insight into whether failures are caused by normal user activity, application configuration issues, or potential malicious activity. Understanding these codes helps SOC analysts prioritize incidents appropriately.

## Evidence

### Screenshot 1 – Query Execution

`10-failed-signins-query.png`

### Screenshot 2 – Query Results

`10-failed-signins-results.png`
