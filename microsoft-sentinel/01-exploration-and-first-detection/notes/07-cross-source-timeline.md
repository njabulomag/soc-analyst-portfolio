# Step 7 – Build a Cross-Source Investigation Timeline

## Objective

Correlate security events from multiple data sources into a single chronological timeline to gain a broader understanding of activity across the environment.

## Query Used

[07-cross-source-timeline.kql](../queries/07-cross-source-timeline.kql)

## Key Findings

The cross-source timeline successfully combined events from multiple security platforms into a single view.

The observed events included:

| Time | Source | Activity | Severity |
|------|--------|----------|----------|
| Jul 24, 2026 | Okta | user.authentication.auth | INFO |
| Jul 24, 2026 | Okta | user.mfa.factor.reset_all | WARN |
| Jul 24, 2026 | Okta | user.mfa.factor.update | WARN |
| Jul 24, 2026 | Okta | user.authentication.auth | INFO |
| Jul 24, 2026 | Okta | user.authentication.auth | INFO |

The timeline demonstrates how Microsoft Sentinel can correlate events from different security products into a unified investigation view. In this execution, the returned events were primarily identity-related activities from Okta, including authentication and multi-factor authentication (MFA) operations.

No high-severity AWS administrative events or CrowdStrike endpoint alerts matched the query filters during the selected time range.

## Evidence

### Timeline Visualization

`07-cross-source-timeline-overview.png`

### Correlated Events

`07-cross-source-timeline-results.png`
