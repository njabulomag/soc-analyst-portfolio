# Step 3 – Explore Palo Alto Firewall Traffic

## Objective

Analyze Palo Alto firewall logs to understand network activity and identify notable traffic patterns.

## Query Used

See:

`queries/03-palo-alto-traffic-overview.kql`

## Key Findings

The firewall activity summary showed three main activities:

- **drop** – 125 events
- **end** – 23 events
- **spyware** – 1 event

The **drop** activity generated the highest number of events, indicating that the firewall blocked a significant amount of network traffic. A single **spyware** event was also observed, suggesting at least one security event that could warrant further investigation.

## Evidence

Screenshot:

`03-palo-alto-traffic-overview.png`
