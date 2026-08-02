# Step 7 – Top User Accounts Investigation

## Objective

Identify the user accounts generating the highest number of Microsoft Entra ID authentication events and establish a baseline of normal account activity.

## Query Used

[07-top-user-accounts.kql](../queries/07-top-user-accounts.kql)

## Query

```kql
EntraIdSignInEvents
| summarize SignInCount = count() by AccountUpn
| order by SignInCount desc
| take 10
```

## Query Explanation

This query summarizes Microsoft Entra ID authentication events by user account.

- **EntraIdSignInEvents** selects authentication logs.
- **summarize** groups sign-ins by account.
- **count()** counts the total number of sign-in events.
- **order by SignInCount desc** sorts the accounts from the highest number of sign-ins to the lowest.
- **take 10** returns the ten most active accounts.

This allows analysts to quickly identify heavily used accounts and establish a baseline of normal authentication activity.

## Findings

The investigation identified the following accounts with the highest authentication activity:

| Account | Sign-ins |
|---------|----------:|
| njabulohlatshwayo... | 3515 |
| Securitydefender... | 473 |
| njabulohlatshwayo... | 1 |

The primary user account generated the highest number of authentication events during the selected period.

A Securitydefender account also generated a significant number of sign-ins, which is consistent with the behavior of a service or security-related account.

No evidence from previous investigations indicated risky sign-ins or unexpected geographic locations, suggesting the observed authentication activity represents the normal operating baseline for this environment.

## Skills Demonstrated

- Microsoft Sentinel
- Microsoft Entra ID
- Identity Monitoring
- Authentication Analysis
- User Activity Analysis
- Kusto Query Language (KQL)
- SOC Investigation

## Key Learning

Reviewing the most active accounts helps SOC analysts identify unusual authentication patterns, distinguish between user and service accounts, and establish a baseline for future investigations.

## Evidence

Screenshot:

`07-top-user-accounts-overview.png`
