# Step 6 – Geographic Sign-in Investigation

## Objective

Analyze Microsoft Entra ID authentication logs to determine the geographic origin of user sign-ins and establish a baseline of normal authentication locations.

## Query Used

[06-signins-by-country.kql](../queries/06-signins-by-country.kql)

## Query

```kql
EntraIdSignInEvents
| summarize SignInCount = count() by Country
| order by SignInCount desc
```

## Query Explanation

This query summarizes Microsoft Entra ID sign-in events by country.

- **EntraIdSignInEvents** selects authentication logs.
- **summarize** groups sign-in events by country.
- **count()** counts the number of sign-ins from each country.
- **order by SignInCount desc** sorts the results from the highest number of sign-ins to the lowest.

This provides a quick overview of the geographic distribution of authentication activity without reviewing thousands of individual sign-in events.

## Findings

The investigation analyzed **3,953 authentication events**.

| Country | Sign-ins |
|---------|---------:|
| ZA (South Africa) | 3953 |

All authentication activity originated from **South Africa (ZA)** during the selected time period.

No sign-ins were observed from foreign countries, indicating a consistent geographic authentication pattern. This establishes a normal baseline for user sign-in locations.

If future investigations identify successful sign-ins from unexpected countries, they should be investigated further to determine whether they are the result of legitimate travel, VPN usage, or potential account compromise.

## Skills Demonstrated

- Microsoft Sentinel
- Microsoft Entra ID
- Identity Monitoring
- Geographic Analysis
- Authentication Investigation
- Kusto Query Language (KQL)
- SOC Investigation

## Key Learning

Geographic analysis helps security analysts establish normal authentication patterns and quickly identify unusual sign-in locations. Establishing a baseline makes it easier to detect impossible travel events, unauthorized access attempts, and compromised accounts.

## Evidence

### Screenshot 1

`06-signins-by-country-query.png`

### Screenshot 2

`06-signins-by-country-results.png`
