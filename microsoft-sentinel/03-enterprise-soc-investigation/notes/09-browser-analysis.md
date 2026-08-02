# Step 9 – Browser Analysis

## Objective

Analyze Microsoft Entra ID authentication logs to identify the browsers and client applications used during authentication and establish a baseline of normal client usage.

## Query Used

[09-browser-analysis.kql](../queries/09-browser-analysis.kql)

## Query

```kql
EntraIdSignInEvents
| summarize SignInCount = count() by Browser
| order by SignInCount desc
```

## Query Explanation

This query summarizes Microsoft Entra ID authentication events by browser or client application.

- **EntraIdSignInEvents** selects authentication logs.
- **summarize** groups authentication events by browser.
- **count()** counts the number of authentication events for each browser.
- **order by SignInCount desc** sorts the results from the highest number of sign-ins to the lowest.

This provides a quick overview of which browsers and client applications are most commonly used for authentication.

## Findings

The investigation identified the following browser and client application activity:

| Browser / Client | Sign-ins |
|-----------------|----------:|
| Rich Client 4.83.1.0 | 2513 |
| Rich Client 4.83.3.0 | 571 |
| Rich Client 4.72.1.0 | 505 |
| Chrome 150.0.0 | 159 |
| Rich Client 4.84.1.0 | 143 |
| Rich Client 4.71.1.0 | 69 |
| Rich Client 4.85.2.0 | 54 |
| Python Requests 2.x | 27 |
| Rich Client 4.86.0.0 | 23 |
| Rich Client 4.82.0.0 | 4 |
| Rich Client 4.66.1.0 | 1 |
| Rich Client 4.78.0.0 | 1 |

Most authentication activity originated from Microsoft Rich Client applications rather than traditional web browsers.

Google Chrome also generated authentication events, indicating browser-based access to Microsoft services.

A small number of authentication events were associated with Python Requests, which may represent automated scripts, integrations, or API-based activity. Such activity should be reviewed to ensure it is expected and authorized.

## Skills Demonstrated

- Microsoft Sentinel
- Microsoft Entra ID
- Browser Analysis
- Client Application Analysis
- Authentication Monitoring
- Kusto Query Language (KQL)
- SOC Investigation

## Key Learning

Browser and client application analysis helps SOC analysts establish a baseline of normal authentication methods. Unexpected browsers, automation tools, or unfamiliar client applications may require additional investigation when correlated with other security indicators.

## Evidence

Screenshot:

`09-browser-analysis-overview.png`
