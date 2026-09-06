# Splunk Authentication Investigation

## Overview

This project demonstrates a Security Operations Center (SOC) investigation using Splunk to analyze authentication and endpoint security activity.

The investigation uses multiple security log sources and Splunk Search Processing Language (SPL) to identify authentication patterns, successful logins, suspicious processes, source IP addresses, devices, users, and MITRE ATT&CK techniques.

## Objectives

* Analyze authentication activity
* Identify successful authentication events
* Investigate endpoint security activity
* Correlate users, devices, processes, and source IP addresses
* Identify potentially suspicious activity
* Practice SPL investigation techniques used by SOC analysts

## Data Sources

The investigation uses:

* `windows-security.csv`
* `crowdstrike.csv`

All investigation data is stored in the Splunk `main` index.

## Investigations

### 01 — Authentication Overview

**Query:**

```text
queries/01-authentication-overview.spl
```

**Notes:**

```text
notes/01-authentication-overview-notes.md
```

**Purpose:**

Review Windows Security authentication activity and identify patterns involving users, devices, source IP addresses, and processes.

---

### 02 — Successful Authentication

**Query:**

```text
queries/02-successful-authentication.spl
```

**Notes:**

```text
notes/02-successful-authentication-notes.md
```

**Evidence:**

```text
screenshots/02-successful-authentication-results.png
```

**Purpose:**

Investigate successful Windows authentication events using Event ID `4624_success`.

The investigation summarizes successful authentication activity by:

* User
* Source IP
* Device
* Process

This helps identify unusual successful authentication patterns and potential credential misuse.

---

### 03 — Endpoint Security Investigation

**Query:**

```text
queries/03-endpoint-security-investigation.spl
```

**Notes:**

```text
notes/03-endpoint-security-investigation-notes.md
```

**Evidence:**

```text
screenshots/03-endpoint-security-investigation-results.png
```

**Purpose:**

Investigate endpoint activity collected from CrowdStrike EDR logs.

The investigation examines:

* Activity type
* Device
* Process
* User
* Source IP
* MITRE ATT&CK technique
* Event frequency

Observed activities include:

* Network connections
* Credential access
* PowerShell activity
* Malware detection

Observed processes include:

* `powershell.exe`
* `rundll32.exe`
* `winword.exe`
* `cmd.exe`

## Investigation Methodology

The investigation follows a basic SOC workflow:

1. Identify the relevant log source.
2. Search the required events.
3. Extract important fields from raw log data.
4. Group related events.
5. Identify unusual or potentially suspicious activity.
6. Document the investigation.
7. Preserve screenshots as investigation evidence.

## Key SPL Techniques Demonstrated

This project demonstrates practical use of:

* `search`
* `rex`
* `stats`
* `sort`
* Field extraction
* Event filtering
* Data aggregation
* Security event investigation

## Security Skills Demonstrated

This project demonstrates practical SOC analyst skills including:

* Log analysis
* Authentication investigation
* Endpoint investigation
* Security event filtering
* Process analysis
* Source IP analysis
* User activity analysis
* MITRE ATT&CK mapping
* Evidence documentation
* SPL development

## Project Structure

```text
01-authentication-investigation/
├── queries/
│   ├── 01-authentication-overview.spl
│   ├── 02-successful-authentication.spl
│   └── 03-endpoint-security-investigation.spl
│
├── screenshots/
│   ├── 01-...
│   ├── 02-successful-authentication-results.png
│   └── 03-endpoint-security-investigation-results.png
│
├── notes/
│   ├── 01-authentication-overview-notes.md
│   ├── 02-successful-authentication-notes.md
│   └── 03-endpoint-security-investigation-notes.md
│
└── README.md
```

## Analyst Takeaway

Authentication and endpoint logs provide valuable evidence for detecting potentially compromised accounts, suspicious processes, unusual source IP addresses, and malicious activity.

Using SPL to extract and correlate these fields allows a SOC analyst to quickly move from raw security logs to actionable investigation data.

