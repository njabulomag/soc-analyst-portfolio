# Step 8 – Create a Multi-Tactic Compromise Detection Rule

## Objective

Develop a custom detection query to identify endpoints that exhibit activity across three or more MITRE ATT&CK tactics within a four-hour period.

## Query Used

[08-multi-tactic-compromise-detection.kql](../queries/08-multi-tactic-compromise-detection.kql)

## Key Findings

The detection query executed successfully but returned **0 matching devices**.

This indicates that, during the selected four-hour lookback period, no endpoint generated high or critical CrowdStrike alerts spanning three or more MITRE ATT&CK tactics.

Although no alerts were returned, the query is suitable for use as a scheduled detection rule and can identify future multi-stage endpoint compromises.

## Evidence

Screenshot:

`08-multi-tactic-compromise-detection-query.png`
