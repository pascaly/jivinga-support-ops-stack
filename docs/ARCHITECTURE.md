# Architecture (high level)

## Goals
- Email-only B2B support (v0.1)
- Deterministic triage and ownership
- Clear incident lifecycle and customer updates
- Automation with human fallback (no black boxes)
- Safe to publish

## Components
- Zammad: ticketing, customer comms, internal notes, basic reporting
- n8n: workflow automation and integrations (email parsing, enrichment, notifications)
- Uptime Kuma: monitoring checks + public status page

## Principles
- Zammad is the single system of record for both Support and Incidents.

## Data flow
```mermaid
flowchart LR
  Email[Inbound Email] --> Zammad[Zammad Ticket]
  Zammad --> n8n[n8n Workflows]
  n8n --> Zammad
  n8n --> Notify[Ops Notifications]
  Uptime[Uptime Kuma Alerts] --> Zammad
  Uptime --> Status[Status Page]
  Zammad --> Customer[Customer Updates]
