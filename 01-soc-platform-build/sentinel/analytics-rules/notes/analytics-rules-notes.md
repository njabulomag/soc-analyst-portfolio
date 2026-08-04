# Analytics Rules Notes

## Rule Name

NRT Security Event Log Cleared

---

## Purpose

To detect Windows Security Event ID 1102, which indicates that the Windows Security Event Log has been cleared. This activity may represent an attempt by an attacker to remove evidence after performing malicious actions.

---

## Detection Type

Near Real-Time (NRT)

---

## Severity

Medium

---

## MITRE ATT&CK

Tactic:
Defense Evasion (TA0005)

Technique:
Indicator Removal on Host (T1070)

---

## Investigation Guidance

Review the user account responsible for clearing the Security Event Log.

Determine whether the action was performed by an authorized administrator.

Review recent authentication activity and system events preceding Event ID 1102.

Investigate any associated alerts or suspicious activity on the affected endpoint.

---

## Business Impact

Unauthorized clearing of the Windows Security Event Log may indicate an attempt to hide malicious activity by removing forensic evidence. Early detection enables SOC analysts to investigate potential compromise before additional attacker actions occur.
