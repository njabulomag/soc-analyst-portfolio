# DE-001 Validation

## Detection

**Detection ID:** DE-001
**Detection Name:** Encoded PowerShell Execution
**Data Source:** CrowdStrikeDetections
**MITRE ATT&CK:** T1059 — Command and Scripting Interpreter

## Validation Objective

The objective of this validation was to determine whether the detection logic could identify encoded PowerShell commands within the CrowdStrike telemetry available in the Microsoft Sentinel laboratory environment.

The detection was developed from existing telemetry rather than artificially generated events.

## Initial Telemetry Validation

The investigation initially examined Windows Security Event ID 4688.

A total of **1,489 Event ID 4688 events** were identified.

However, the available normalized process fields did not contain sufficient information for reliable process-based detection.

The investigation therefore pivoted to the `CrowdStrikeDetections` table.

## CrowdStrike Behaviour Discovery

The CrowdStrike dataset contained **54 detection records**.

The `Behaviors` field contained structured JSON data.

Relevant fields identified included:

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

## Behaviour Identified

The CrowdStrike telemetry contained **12 T1059 — Command and Scripting Interpreter** behaviours.

Inspection of the individual behaviours showed that the events were classified as:

**Malicious PowerShell Execution**

Further analysis of the command-line data identified PowerShell executions using:

```text
-enc
```

The encoded PowerShell command was associated with:

```text
Invoke-WebRequest
```

## Validation Query

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

## Validation Result

The detection returned:

**5 historical matches**

The observed confidence values were:

* 95
* 93
* 92
* 72
* 60

All five events involved `powershell.exe` and an encoded PowerShell command.

## Observed Command Pattern

The command-line pattern observed was:

```text
powershell.exe -enc <Base64 encoded command>
```

The encoded content observed in the laboratory telemetry decoded to:

```text
Invoke-WebRequest
```

## Detection Assessment

### Result: PASS

The detection successfully identified the encoded PowerShell execution pattern present in the historical CrowdStrike telemetry.

The detection is not dependent on the exact Base64 payload. Instead, it identifies the execution pattern through:

1. CrowdStrike T1059 classification
2. `powershell.exe`
3. `-enc` or `-encodedcommand`

## Limitations

This validation uses historical laboratory telemetry.

The five matches demonstrate that the detection logic can identify the observed pattern, but they do not demonstrate that five new incidents were generated.

Incident-generation testing will be performed separately after the Sentinel Analytics Rule is configured.

The underlying laboratory data also contains synthetic indicators and simulated endpoint behaviours. These will be clearly identified as laboratory telemetry in the final portfolio documentation.

## Next Validation Stage

The next stage is to create the Microsoft Sentinel Analytics Rule and determine whether the detection can generate a Sentinel incident from matching telemetry.

The incident will then be investigated as a SOC analyst would investigate an encoded PowerShell alert.

## Validation Lifecycle

```text
Telemetry Discovery
        ↓
Schema Investigation
        ↓
Behaviour Identification
        ↓
Detection Development
        ↓
Historical Validation
        ↓
5 Matches Confirmed
        ↓
Analytics Rule
        ↓
Incident Validation
        ↓
SOC Investigation
        ↓
Response and Tuning
```
