# Telemetry Strategy

## Purpose

This document defines the initial telemetry onboarding priorities for the simulated environment.

The goal is to prioritize data sources that provide strong detection and investigation value without ingesting every available event by default.

## Prioritization Criteria

Telemetry sources are evaluated based on:

- Detection value
- Investigation value
- Expected event volume
- Onboarding complexity
- Availability and licensing
- Ability to correlate with other sources

## Available Data Sources

| Source | Platform | Main telemetry |
|---|---|---|
| Identity | Microsoft Entra ID | Sign-ins, audit activity, authentication events |
| Email and collaboration | Microsoft 365 | Exchange, mailbox, SharePoint and user audit activity |
| Endpoint | Microsoft Defender for Endpoint | Alerts, process, network and device activity |
| Endpoint management | Microsoft Intune | Device compliance and configuration changes |
| Operating systems | Windows and Linux | Authentication, process and system events |
| Network | Palo Alto Networks | Traffic, threat, VPN and administrative events |
| Cloud | AWS | CloudTrail and selected service logs |

## Initial Onboarding Priority

| Priority | Data source | Reason |
|---:|---|---|
| 1 | Microsoft Entra ID | Primary identity source and required for account-compromise investigations |
| 2 | Microsoft 365 Audit | Supports mailbox abuse, BEC and user-activity investigations |
| 3 | Microsoft Defender for Endpoint | Provides endpoint execution, network and device investigation context |
| 4 | Windows Security telemetry | Adds authentication and system-level visibility not fully covered by EDR |
| 5 | Palo Alto firewall and VPN | Adds network, perimeter and remote-access visibility |
| 6 | Linux telemetry | Required for the smaller Linux server environment |
| 7 | AWS telemetry | Lower initial priority because the AWS environment is limited |

## Onboarding Approach

Each source will be onboarded through the same process:

1. Identify required security and investigation use cases.
2. Select the relevant log types.
3. Define required fields.
4. Estimate expected data volume.
5. Configure ingestion and normalization.
6. Validate data quality.
7. Build and test detections.
8. Document operational ownership and monitoring.

## Volume Strategy

Not every available event will be ingested automatically.

High-volume sources such as endpoint process telemetry and firewall allowed traffic will be evaluated against their detection and investigation value before full ingestion.

Filtering should be based on documented requirements rather than storage cost alone.

## First Implementation

The first telemetry onboarding project will focus on Microsoft Entra ID.

Detailed log selection, field requirements, ingestion, normalization and validation will be documented separately.