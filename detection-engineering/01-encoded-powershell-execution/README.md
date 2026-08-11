# DE-001 — Encoded PowerShell Execution

## 1. Detection Overview

**Detection ID:** DE-001
**Detection Name:** Encoded PowerShell Execution
**Status:** Validation completed — Analytics Rule pending
**Data Source:** CrowdStrikeDetections
**Platform:** Microsoft Sentinel
**MITRE ATT&CK Tactic:** Execution
**MITRE ATT&CK Technique:** T1059 — Command and Scripting Interpreter

## 2. Objective

The objective of this detection is to identify suspicious PowerShell execution where PowerShell is launched with an encoded command.

Encoded PowerShell can be used to hide command content from analysts and security controls. In this investigation, CrowdStrike telemetry already contained multiple behaviours classified as malicious PowerShell execution.

The detection was therefore developed from existing telemetry rather than from artificially generated events.

## 3. Initial Telemetry Investigation

The investigation initially began with Windows Security Event ID 4688.

A total of **1,489 Event ID 4688 records** were identified in the `SecurityEvent` table.

However, the normalized process-related fields did not provide sufficient information for reliable process-based detection engineering.

The following fields were investigated:

* `NewProcessName`
* `Process`
* `CommandLine`
* `ParentProcessName`
* `EventData`

The available records did not provide sufficient populated process or command-line information.

### Finding

Windows Event ID 4688 was confirmed to exist, but the available normalized telemetry was insufficient for this detection.

Rather than forcing a detection against incomplete data, the investigation pivoted to CrowdStrike endpoint telemetry.

## 4. CrowdStrike Telemetry Discovery

The `CrowdStrikeDetections` table contained **54 detection records**.

The `Behaviors` field contained structured JSON with useful detection information, including:

* Behavior ID
* Timestamp
* Severity
* Confidence
* Tactic
* Technique
* Technique ID
* Display name
* Filename
* File path
* Command line
* SHA-256
* Process ID
* Parent process ID

This provided significantly better telemetry for detection engineering.

## 5. Behaviour Landscape

An analysis of the CrowdStrike behaviours identified several MITRE ATT&CK techniques:

| Technique | Behaviour                                 | Occurrences | Max Severity |
| --------- | ----------------------------------------- | ----------: | -----------: |
| T1059     | Command and Scripting Interpreter         |          12 |           80 |
| T1005     | Data from Local System                    |           9 |           40 |
| T1003     | OS Credential Dumping                     |           9 |           80 |
| T1071     | Application Layer Protocol                |           6 |           80 |
| T1562     | Impair Defenses                           |           6 |           60 |
| T1486     | Data Encrypted for Impact                 |           5 |           80 |
| T1021     | Remote Services                           |           3 |           60 |
| T1204.002 | User Execution: Malicious File            |           1 |           80 |
| T1003.001 | OS Credential Dumping: LSASS Memory       |           1 |           80 |
| T1071.001 | Application Layer Protocol: Web Protocols |           1 |           80 |

This demonstrated that the environment contained telemetry covering multiple stages of the MITRE ATT&CK lifecycle.

## 6. T1059 Investigation

The 12 T1059 events were examined individually.

Although the telemetry was classified under the parent technique:

**T1059 — Command and Scripting Interpreter**

the CrowdStrike `DisplayName` field identified the observed behaviour as:

**Malicious PowerShell Execution**

The events had:

* Severity: 80
* Confidence range: 60–95
* Executable: `powershell.exe` or related lab artefacts

## 7. Encoded PowerShell Discovery

The command-line data was extracted from the `Behaviors` JSON.

Multiple events contained:

```text
powershell.exe -enc <Base64 encoded command>
```

The observed encoded command decoded to:

```text
Invoke-WebRequest
```

The identified encoded PowerShell events included:

| Behavior ID | Confidence | File           |
| ----------- | ---------: | -------------- |
| 3291034226  |         95 | powershell.exe |
| 8052386461  |         93 | powershell.exe |
| 9485725773  |         92 | powershell.exe |
| 8903909133  |         72 | powershell.exe |
| 5942384035  |         60 | powershell.exe |

This produced **5 historical matches** for the encoded PowerShell detection pattern.

## 8. Detection Logic

The detection identifies CrowdStrike T1059 behaviours where:

1. The CrowdStrike behaviour is classified as T1059.
2. The executable is `powershell.exe`.
3. The command line contains `-enc` or `-encodedcommand`.

The detection intentionally does not rely on a single Base64 value.

This makes the rule more general and avoids detecting only the specific lab command observed during validation.

## 9. Validation Query

```kusto
CrowdStrikeDetections
| where isnotempty(Behaviors)
| extend B = todynamic(Behaviors)
| where tostring(B.technique_id) == "T1059"
| extend
    BehaviorId = tostring(B.behavior_id),
    Severity = toint(B.severity),
    Confidence = toint(B.confidence),
    Technique = tostring(B.technique),
    FileName = tostring(B.filename),
    CommandLine = tostring(B.cmdline),
    SHA256 = tostring(B.sha256),
    ProcessId = tostring(B.process_id),
    ParentProcessId = tostring(B.parent_process_id),
    BehaviorTimestamp = todatetime(B.timestamp)
| where FileName =~ "powershell.exe"
| where CommandLine has_any ("-enc", "-encodedcommand")
| project
    TimeGenerated,
    BehaviorId,
    Severity,
    Confidence,
    Technique,
    FileName,
    CommandLine,
    SHA256,
    ProcessId,
    ParentProcessId,
    BehaviorTimestamp
| order by TimeGenerated desc
```

## 10. Validation Result

The validation query returned **5 historical matches**.

This confirms that the detection logic successfully identifies the encoded PowerShell behaviour present in the CrowdStrike telemetry.

The historical matches had confidence values ranging from **60 to 95**.

## 11. Related Behaviour

During the same telemetry investigation, several CrowdStrike behaviours involving `report.exe` were identified.

Examples included executions from user Downloads directories such as:

```text
C:\Users\mirage\Downloads\report.exe
C:\Users\spatel\Downloads\report.exe
C:\Users\jliu\Downloads\report.exe
C:\Users\aturner\Downloads\report.exe
C:\Users\ceo\Downloads\report.exe
```

A separate CrowdStrike behaviour also identified:

**T1204.002 — User Execution: Malicious File**

with `report.exe`.

These events may be related to the PowerShell activity, but this relationship has **not yet been established**. Further investigation is required before treating them as one attack chain.

## 12. Important Telemetry Note

The observed SHA-256 value associated with one `report.exe` event was:

```text
e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855
```

This value is associated with an empty input and indicates that the laboratory telemetry may contain synthetic or simulated endpoint data.

The portfolio will therefore document these events as **lab telemetry** and will not claim that the associated files represent confirmed real-world malware.

## 13. Current Status

### Completed

* [x] Windows Security telemetry reviewed
* [x] Event ID 4688 availability confirmed
* [x] Limitations of 4688 telemetry documented
* [x] CrowdStrike telemetry identified
* [x] CrowdStrike behaviour JSON inspected
* [x] MITRE T1059 behaviour identified
* [x] Malicious PowerShell behaviour identified
* [x] Encoded PowerShell commands identified
* [x] Command-line evidence extracted
* [x] Detection query developed
* [x] Detection query validated
* [x] Five historical matches confirmed

### Pending

* [ ] Create Sentinel Analytics Rule
* [ ] Configure incident generation
* [ ] Validate incident creation
* [ ] Investigate generated/observed incident
* [ ] Enrich indicators with VirusTotal
* [ ] Map investigation to MITRE ATT&CK
* [ ] Document investigation timeline
* [ ] Document incident response actions
* [ ] Tune detection
* [ ] Capture evidence screenshots
* [ ] Final detection review

## 14. Detection Engineering Principle

This detection was developed using an evidence-first approach.

The investigation did not assume that the Windows Security telemetry contained the required fields. When the initial data source proved insufficient, the investigation pivoted to CrowdStrike telemetry.

The final detection was based on a behaviour actually observed in the environment.

**Evidence → Detection → Validation → Investigation → Response → Tuning**

This approach will be used for subsequent detection-engineering projects.
