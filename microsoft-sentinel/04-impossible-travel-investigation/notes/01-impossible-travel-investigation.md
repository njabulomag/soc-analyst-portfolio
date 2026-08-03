# Investigation 01 – Impossible Travel Investigation

## Objective

Investigate Microsoft Entra ID sign-in logs to determine whether any user authenticated from multiple countries during the selected investigation period. Authentication from multiple geographic locations may indicate impossible travel and could be a sign of compromised credentials.

---

## Query Used

[01-impossible-travel-investigation.kql](../queries/01-impossible-travel-investigation.kql)

```kql
EntraIdSignInEvents
| summarize
    Countries = dcount(Country),
    CountryList = make_set(Country)
by AccountUpn
| order by Countries desc
```

---

## Query Explanation

### EntraIdSignInEvents

This table contains Microsoft Entra ID authentication logs.

Each record includes information such as:

- User Account
- Country
- Browser
- Operating System
- IP Address
- Time of Sign-in

---

### summarize

The **summarize** operator groups multiple sign-in records into a single summary for each user.

Instead of displaying thousands of authentication events, it creates one summarized record per account.

---

### dcount(Country)

The **dcount()** function means **Distinct Count**.

It counts the number of unique countries from which each account authenticated.

Example:

ZA

ZA

ZA

US

UK

The distinct count is **3** because there are three unique countries.

---

### make_set(Country)

The **make_set()** function creates a list of all unique countries associated with each account.

Instead of only showing:

Countries = 3

it also displays:

["ZA","US","UK"]

making investigations easier.

---

### by AccountUpn

Groups the information by user account.

Each account receives its own summary.

---

### order by Countries desc

Sorts the results from the highest number of countries to the lowest.

This allows analysts to quickly identify accounts authenticating from multiple geographic locations.

---

## Investigation Findings

The investigation returned the following results:

| Account | Countries | Country List |
|---------|----------:|--------------|
| njabulohlatshwayo... | 1 | ["ZA"] |
| Securitydefender... | 1 | ["ZA"] |
| ddd66a7d-3caf-4c... | 1 | ["ZA"] |

Every observed account authenticated from only one country.

The only country observed during the investigation was:

**South Africa (ZA)**

---

## Analysis

Impossible travel investigations are designed to identify users authenticating from geographically distant locations within an unrealistic period of time.

The authentication data showed that every observed account authenticated only from South Africa.

No geographic anomalies or suspicious authentication patterns were identified.

---

## Conclusion

No evidence of impossible travel was identified during the selected investigation period.

All observed authentication activity originated from South Africa (ZA), indicating consistent geographic authentication behavior.

---

## Skills Demonstrated

- Microsoft Sentinel
- Microsoft Entra ID
- Identity Monitoring
- Authentication Analysis
- Geographic Analysis
- Kusto Query Language (KQL)
- SOC Investigation

---

## Evidence

Screenshot:

`01-impossible-travel-investigation.png`
