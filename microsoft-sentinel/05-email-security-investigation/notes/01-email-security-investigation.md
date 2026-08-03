# Investigation 01 – Email Security Investigation

## Objective

Investigate recent email activity recorded in Microsoft Defender to determine whether any suspicious or potentially malicious emails were delivered to users.

---

## Query Used

[01-email-security-investigation.kql](../queries/01-email-security-investigation.kql)

```kql
EmailEvents
| project
    TimeGenerated,
    SenderFromAddress,
    RecipientEmailAddress,
    Subject,
    DeliveryAction,
    DeliveryLocation
| order by TimeGenerated desc
```

---

## Query Explanation

### EmailEvents

The **EmailEvents** table contains information about emails processed by Microsoft Defender for Office 365.

Each record contains details about the sender, recipient, subject, delivery action and delivery location.

---

### project

The **project** operator selects only the columns required for the investigation.

The investigation displays:

- TimeGenerated
- SenderFromAddress
- RecipientEmailAddress
- Subject
- DeliveryAction
- DeliveryLocation

---

### order by TimeGenerated desc

Sorts the emails from newest to oldest, allowing the most recent activity to be reviewed first.

---

## Investigation Findings

Three recent email events were identified.

| Sender | Subject | Delivery Action | Delivery Location |
|---------|----------|----------------|------------------|
| mssecurity-noreply@microsoft... | Your weekly PIM digest | Delivered | Inbox |
| mssecurity-noreply@microsoft... | New recommendation... | Delivered | Inbox |
| microsoft365@notifications... | Start using your free Microsoft... | Delivered | Inbox |

---

## Analysis

The reviewed email activity consisted of legitimate Microsoft notification emails.

During the investigation:

- All emails originated from trusted Microsoft notification services.
- No suspicious sender domains were identified.
- All emails were successfully delivered.
- No emails were quarantined or blocked.
- No phishing indicators were observed.

The investigation did not identify any malicious email activity.

---

## Conclusion

The reviewed email events appear to be legitimate Microsoft service notifications.

No suspicious email activity, phishing attempts or malicious delivery actions were identified during the selected investigation period.

---

## Skills Demonstrated

- Microsoft Sentinel
- Microsoft Defender for Office 365
- Email Security Investigation
- Email Log Analysis
- Kusto Query Language (KQL)
- SOC Investigation

---

## Evidence

### Screenshot 1

`01-email-security-query.png`

### Screenshot 2

`02-email-security-results.png`
