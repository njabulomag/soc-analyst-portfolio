# Step 9 – Create and Verify the Custom Detection Rule

## Objective

Create a scheduled custom detection rule based on the validated KQL query to automatically identify endpoints exhibiting activity across multiple MITRE ATT&CK tactics.

## Detection Rule Configuration

| Setting | Value |
|---------|-------|
| Name | Lab Stage E1 - Multi-Tactic Compromise on Single Device |
| Severity | High |
| Frequency | Every Hour |
| Lookback | 4 Hours |
| Entity Mapping | Device → HostName → DeviceName |

## Verification

The detection rule was successfully created in Microsoft Defender.

The rule is scheduled to execute automatically every hour and will alert when a device generates high or critical CrowdStrike alerts spanning three or more MITRE ATT&CK tactics within the configured lookback period.

## Skills Demonstrated

- Detection Engineering
- Microsoft Defender XDR
- Microsoft Sentinel
- Kusto Query Language (KQL)
- Entity Mapping
- MITRE ATT&CK
- Alert Configuration

## Evidence

- `09-alert-details.png`
- `09-entity-mapping.png`
- `09-actions-page.png`
- `09-review-page.png`
- `09-detection-rule-created.png`
