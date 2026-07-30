# Step 1 – Table Discovery

## Objective

Identify the data tables available in the Microsoft Sentinel Training Lab to understand what telemetry can be used for threat hunting and detection engineering.

## Query Used

See:

`queries/01-discover-tables.kql`

## Observations

After running the query, I confirmed that my environment contains multiple data tables with security telemetry.

Some of the first tables returned were:

- ExposureGraphNodes
- SecurityEvent
- GraphAPIAuditEvents
- EntraIdSignInEvents
- IdentityInfo

These tables indicate that the lab contains identity, endpoint, audit, and Windows security event data that can be used for investigations and threat hunting.

## Evidence

Screenshot:

`01-discover-tables-results.png`
