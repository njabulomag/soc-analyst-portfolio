# SOC Case 001 — Encoded PowerShell Execution Investigation

## 1. Case Overview

**Case ID:** SOC-001
**Detection ID:** DE-001
**Case Name:** Encoded PowerShell Execution
**Status:** Investigation in progress
**Environment:** Microsoft Sentinel SOC Laboratory
**Primary Endpoint Source:** CrowdStrike
**Primary Data Table:** `CrowdStrikeDetections`
**MITRE ATT&CK Technique:** T1059 — Command and Scripting Interpreter
**Observed Behaviour:** Malicious PowerShell Execution

This investigation was initiated from CrowdStrike endpoint telemetry discovered during development and validation of Detection Engineering rule DE-001.

No artificial incident was created.

The case is based on historical security telemetry already present in the laboratory environment.

---

## 2. Executive Summary

CrowdStrike telemetry identified multiple behaviours classified as **Malicious PowerShell Execution**.

Further investigation identified five PowerShell behaviours where `powershell.exe` was executed with an encoded command parameter:

```text
powershell.exe -enc <Base64 encoded command>
```

The observed encoded command was decoded as:

```text
Invoke-WebRequest
```

The activity therefore represents suspicious PowerShell execution involving encoded command content and web-request functionality.

Additional CrowdStrike telemetry identified executions of:

```text
report.exe
```

from multiple users' Downloads directories.

A separate behaviour classified the `report.exe` activity as:

**T1204.002 — User Execution: Malicious File**

The relationship between the PowerShell activity and `report.exe` has not yet been conclusively established.

---

## 3. Investigation Trigger

The investigation originated from the detection-engineering process.

The initial telemetry search identified:

**54 CrowdStrike detection records.**

A behaviour analysis identified:

**12 T1059 — Command and Scripting Interpreter behaviours.**

Inspection of the individual behaviours showed:

**Malicious PowerShell Execution**

This led to the development and validation of DE-001.

The validated detection returned:

**5 historical encoded PowerShell matches.**

---

## 4. Initial Windows Telemetry Investigation

Before pivoting to CrowdStrike, Windows Security Event ID 4688 was investigated.

The `SecurityEvent` table contained:

**1,489 Event ID 4688 events.**

However, the available normalized process fields did not provide sufficient reliable command-line and process information for this investigation.

The investigation therefore pivoted to CrowdStrike endpoint telemetry.

### Investigation principle

The data source was not forced to support a detection it could not reliably support.

Instead:

```text
Windows Security
      ↓
Insufficient process evidence
      ↓
CrowdStrike telemetry
      ↓
Structured behaviour evidence
```

---

## 5. CrowdStrike Evidence

The CrowdStrike `Behaviors` field contained structured JSON information.

Relevant fields included:

* `behavior_id`
* `severity`
* `confidence`
* `tactic`
* `technique`
* `technique_id`
* `display_name`
* `filename`
* `filepath`
* `cmdline`
* `sha256`
* `process_id`
* `parent_process_id`
* `timestamp`

This provided sufficient information to investigate the behaviour at the endpoint level.

---

## 6. Encoded PowerShell Evidence

The following behaviours were identified as encoded PowerShell execution:

| Behavior ID | Confidence | Executable     |
| ----------- | ---------: | -------------- |
| 3291034226  |         95 | powershell.exe |
| 8052386461  |         93 | powershell.exe |
| 9485725773  |         92 | powershell.exe |
| 8903909133  |         72 | powershell.exe |
| 5942384035  |         60 | powershell.exe |

The observed command pattern was:

```text
powershell.exe -enc <Base64 encoded command>
```

The encoded command decoded to:

```text
Invoke-WebRequest
```

This indicates that PowerShell was being used to perform web-request functionality while hiding the command content through Base64 encoding.

---

## 7. Suspicious Characteristics

The following characteristics increase the investigative significance of the activity:

### Encoded command execution

The use of:

```text
-enc
```

obscures the actual PowerShell command from casual inspection.

### PowerShell execution

PowerShell provides extensive access to Windows functionality and can be abused for execution, discovery, download, persistence, and post-exploitation.

### Web request

The decoded command:

```text
Invoke-WebRequest
```

indicates network retrieval or web-request functionality.

The exact destination was not available from the current extracted command line and therefore has not been attributed.

### CrowdStrike classification

The source telemetry itself classified the behaviour as:

**Malicious PowerShell Execution**

This is additional supporting evidence.

---

## 8. Related `report.exe` Activity

Additional CrowdStrike behaviours identified multiple executions of `report.exe`.

Observed paths included:

```text
C:\Users\ceo\Downloads\report.exe
C:\Users\mirage\Downloads\report.exe
C:\Users\aturner\Downloads\report.exe
C:\Users\spatel\Downloads\report.exe
C:\Users\jliu\Downloads\report.exe
```

These executions occurred in user Downloads directories.

A separate CrowdStrike behaviour identified:

**T1204.002 — User Execution: Malicious File**

associated with `report.exe`.

### Investigation hypothesis

One possible scenario is:

```text
User receives/downloads file
        ↓
report.exe executed
        ↓
Malicious behaviour triggered
        ↓
PowerShell execution
        ↓
Encoded command
        ↓
Invoke-WebRequest
```

However, this remains a **hypothesis**.

The available evidence does not yet prove that the `report.exe` events and the encoded PowerShell events belong to the same attack sequence.

---

## 9. Evidence Correlation Requirements

To establish whether the events belong to the same attack chain, the following evidence must be correlated:

* Timestamp
* Endpoint/hostname
* User/account
* Process ID
* Parent process ID
* File path
* SHA-256
* Command line
* Network destination
* Related CrowdStrike behaviours

The investigation will not claim a relationship until these fields provide supporting evidence.

---

## 10. MITRE ATT&CK Mapping

### T1059 — Command and Scripting Interpreter

**Tactic:** Execution

Observed behaviour:

```text
Malicious PowerShell Execution
```

### T1204.002 — User Execution: Malicious File

**Tactic:** Execution

Observed artefact:

```text
report.exe
```

### Other Relevant Techniques in the Environment

The wider CrowdStrike dataset also contained:

| Technique | Tactic              |
| --------- | ------------------- |
| T1003     | Credential Access   |
| T1005     | Collection          |
| T1071     | Command and Control |
| T1562     | Defense Evasion     |
| T1486     | Impact              |
| T1021     | Lateral Movement    |

These techniques are present in the environment but have **not been attributed to SOC-001** without additional evidence.

---

## 11. Indicator of Compromise

One `report.exe` event contained the following SHA-256:

```text
e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855
```

This value corresponds to an empty input hash.

Because the laboratory telemetry may contain simulated or synthetic data, this indicator must not automatically be treated as a confirmed malware hash.

External reputation enrichment will be performed separately.

---

## 12. Current Assessment

### Finding

**Suspicious encoded PowerShell execution confirmed.**

### Confidence

**High**

Supporting evidence:

* CrowdStrike classified the behaviour as malicious.
* PowerShell was executed.
* Encoded command execution was observed.
* Five separate encoded PowerShell behaviours were identified.
* The encoded content decoded to `Invoke-WebRequest`.

### Current severity assessment

**High**

The activity warrants investigation because encoded PowerShell combined with web-request functionality is consistent with techniques commonly used during malicious execution and payload retrieval.

This is a laboratory assessment and not a claim that an actual compromise occurred.

---

## 13. Sentinel Analytics Rule Status

DE-001 was deployed as a Microsoft Sentinel Scheduled Analytics Rule.

The rule was successfully created and enabled.

Historical KQL validation returned:

**5 matching behaviours.**

However, Sentinel did not generate a new incident from the historical data.

The rule-run history remained unavailable after the platform's indicated run-history waiting period.

Therefore:

```text
Detection logic: PASS
Historical validation: PASS
Analytics rule deployment: PASS
New incident generation: NOT OBSERVED
```

This case therefore proceeds as a **historical SOC investigation** rather than a newly generated Sentinel incident.

---

## 14. Investigation Limitations

The following limitations are currently known:

1. The CrowdStrike telemetry is historical.
2. Sentinel did not generate a new incident from the historical events.
3. The original PowerShell network destination is not currently available in the extracted command line.
4. Reliable host/account correlation has not yet been established.
5. The relationship between `report.exe` and PowerShell has not been proven.
6. Some laboratory telemetry may be synthetic or simulated.

These limitations will be clearly documented rather than hidden.

---

## 15. Next Investigation Actions

The next stages are:

### 1. VirusTotal enrichment

Investigate the available SHA-256 indicator and determine whether external reputation data provides useful context.

### 2. Process correlation

Investigate the parent and child process relationships for the PowerShell and `report.exe` behaviours.

### 3. Network investigation

Search available network telemetry for web-request activity associated with the PowerShell execution.

### 4. User investigation

Determine whether the users associated with `report.exe` activity can be correlated with the PowerShell behaviours.

### 5. Timeline reconstruction

Build a chronological attack timeline.

### 6. MITRE ATT&CK analysis

Map only techniques supported by evidence.

### 7. Response assessment

Determine appropriate containment, eradication, and recovery actions for the laboratory scenario.

### 8. Detection tuning

Use investigation findings to determine whether DE-001 requires tuning.

---

## 16. Investigation Lifecycle

```text
Detection Engineering
        ↓
CrowdStrike Behaviour
        ↓
Encoded PowerShell Detection
        ↓
Historical Validation
        ↓
SOC Investigation
        ↓
Indicator Enrichment
        ↓
Process Correlation
        ↓
Network Investigation
        ↓
Timeline Reconstruction
        ↓
MITRE ATT&CK
        ↓
Response Assessment
        ↓
Detection Tuning
        ↓
Lessons Learned
```

---

## 17. Evidence Philosophy

This case intentionally distinguishes between:

**Observed evidence**

and:

**Analyst hypothesis**

Observed evidence is documented as fact.

Potential attack chains are explicitly labelled as hypotheses until supported by additional telemetry.

No incidents, malware classifications, network destinations, compromised accounts, or attack relationships will be invented for portfolio purposes.

The objective is to demonstrate the actual analytical process of a SOC analyst working with imperfect security telemetry.
