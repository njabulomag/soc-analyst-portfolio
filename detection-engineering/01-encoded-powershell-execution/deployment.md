# DE-001 — Sentinel Analytics Rule Deployment

## 1. Deployment Overview

**Detection ID:** DE-001
**Detection Name:** Encoded PowerShell Execution
**Platform:** Microsoft Sentinel
**Data Source:** CrowdStrikeDetections
**Rule Type:** Scheduled query rule
**Status:** Enabled
**Severity:** High

The validated detection was deployed as a Microsoft Sentinel Analytics Rule.

The purpose of this stage was to move the detection from a validated KQL query into the Sentinel detection engine and determine whether it could generate alerts and incidents.

---

## 2. Detection Logic

The deployed rule uses the validated DE-001 detection query stored at:

```text
detection-engineering/01-encoded-powershell-execution/detection.kql
```

The detection identifies CrowdStrike behaviours classified as:

**T1059 — Command and Scripting Interpreter**

and filters for PowerShell execution where the command line contains:

```text
-enc
```

or:

```text
-encodedcommand
```

---

## 3. Rule Configuration

### Rule name

```text
DE-001 - Encoded PowerShell Execution
```

### Severity

```text
High
```

### Schedule

```text
Run query every: 5 minutes
```

### Lookback period

```text
1 hour
```

### Alert threshold

```text
Generate an alert when the query returns more than 0 results
```

### Incident creation

```text
Enabled
```

---

## 4. MITRE ATT&CK Mapping

The detection was mapped to:

**Tactic:** Execution

**Technique:**

```text
T1059 - Command and Scripting Interpreter
```

The underlying observed behaviour was specifically associated with malicious PowerShell execution.

---

## 5. Alert Enhancement

The rule was configured to provide useful investigation context to the analyst.

### Entity mapping

File-related telemetry was mapped where supported by the available fields.

The detection did not force host or account mappings because reliable host/account fields were not available in the current CrowdStrike behaviour dataset.

This prevents inaccurate entity enrichment.

### Custom details

The following fields were configured as custom alert details:

```text
BehaviorId
Severity
Confidence
Technique
CommandLine
FileName
SHA256
ProcessId
ParentProcessId
```

These fields allow an analyst to inspect the detection evidence directly from the alert.

---

## 6. Alert Details

### Alert name

```text
DE-001 - Encoded PowerShell Execution
```

### Description

```text
CrowdStrike telemetry identified PowerShell execution using an encoded command. The detection is based on T1059 Command and Scripting Interpreter activity where powershell.exe is executed with -enc or -encodedcommand. Historical validation identified five matching behaviours.
```

### Tactic

```text
Execution
```

### Technique

```text
T1059 - Command and Scripting Interpreter
```

---

## 7. Alert Grouping Decision

For the initial deployment, alert grouping was disabled.

The rule was configured to:

```text
Don't group alerts
```

### Reason

The purpose of the first deployment is detection validation.

Keeping alerts separate makes it easier to determine:

* which behaviour triggered an alert
* which command line was involved
* which process was involved
* which confidence score was assigned
* which behaviour ID generated the alert

After validation, grouping can be evaluated as part of detection tuning.

---

## 8. Automated Response

No automated response actions were configured.

The initial workflow intentionally follows:

```text
Detection
    ↓
Alert
    ↓
Incident
    ↓
Analyst investigation
    ↓
Enrichment
    ↓
Response decision
```

Automatic containment was not enabled because the detection is still undergoing validation.

---

## 9. Initial Deployment Result

After deployment, no incident was immediately visible.

This does **not** indicate that the detection query failed.

The detection query had already been independently validated and returned:

```text
5 historical matches
```

The Sentinel Analytics Rule was successfully created and enabled.

---

## 10. Rule Run History

When checking the rule's run history, Sentinel displayed:

```text
No records for rule runs yet
```

The interface indicated that rule runs will become available **90 minutes after the run completes**.

Therefore, at the time of this validation, sufficient rule-run history was not yet available to determine:

* whether the scheduled rule had executed
* how many results were returned
* whether an alert had been generated
* whether an incident had been created

---

## 11. Current Assessment

### KQL Detection

**PASS**

The query successfully identified five historical encoded PowerShell behaviours.

### Analytics Rule Deployment

**PASS**

The Sentinel Analytics Rule was successfully created and enabled.

### Alert Generation

**PENDING**

Insufficient rule-run history was available at the time of validation.

### Incident Generation

**PENDING**

No incident had been generated at the time of the initial deployment check.

### Overall Status

```text
DEPLOYED — AWAITING RULE-RUN VALIDATION
```

---

## 12. Next Validation Stage

The next validation will examine the Analytics Rule after Sentinel has accumulated sufficient run history.

The following will be checked:

1. Rule execution status
2. Query result count
3. Alert generation
4. Incident creation
5. Incident evidence
6. Entity enrichment
7. Custom alert details
8. Investigation timeline

If an incident is generated, the investigation will proceed using a SOC analyst workflow.

---

## 13. Portfolio Evidence

Evidence to be captured during the next stage:

* Analytics Rule configuration
* Enabled rule status
* Rule run history
* Generated alert
* Generated incident
* Incident entities
* Incident evidence
* Investigation timeline

Screenshots will only be captured when they provide meaningful evidence of the detection lifecycle.

---

## 14. Detection Lifecycle

```text
Telemetry Discovery
        ↓
Detection Development
        ↓
Historical Validation
        ↓
KQL PASS
        ↓
Sentinel Analytics Rule
        ↓
Rule Deployment
        ↓
Rule Run Validation
        ↓
Alert Generation
        ↓
Incident Generation
        ↓
SOC Investigation
        ↓
Threat Intelligence Enrichment
        ↓
MITRE ATT&CK Analysis
        ↓
Response
        ↓
Detection Tuning
```

## 15. Final Rule-Run Validation

After allowing sufficient time for Microsoft Sentinel to populate the rule-run history, no rule-run records, alerts, or incidents were created.

### Final Result

* Detection query validation: **PASS**
* Historical matches: **5**
* Analytics Rule deployment: **PASS**
* Rule status: **Enabled**
* New alert generation: **Not observed**
* New incident generation: **Not observed**

### Root Cause Assessment

The CrowdStrike behaviors used to validate the detection are historical telemetry. The observed events have historical `TimeGenerated` values and fall outside the scheduled rule's active lookback window.

Microsoft Sentinel scheduled query rules evaluate events that occur within the configured lookback period. Creating the rule does not cause historical events outside that window to be replayed as new alerts or incidents.

### Conclusion

DE-001 successfully detects the encoded PowerShell pattern in historical CrowdStrike telemetry and returned five validated matches. The Analytics Rule was successfully deployed, but no new alert or incident was generated because the matching events were historical rather than newly ingested telemetry.

This result was documented as an environmental validation limitation rather than a detection logic failure.

