# Jivinga Support + Incident Ops Stack (Blueprint)

A review-friendly reference architecture and ops blueprint for B2B support and incident handling using:
- Zammad (ticketing)
- n8n (automation)
- Uptime Kuma (monitoring + status page)

This repository is safe to publish:
- no proprietary application code
- no production configuration
- no customer data
- no secrets

## Problem
Early-stage B2B products often run support via email without:
- reliable triage and ownership
- consistent severity and SLA handling
- clear incident process and customer updates
- automation guardrails (dedup, loops, attachment handling)

## Solution (v0.1)
Email-only B2B support with:
1) Zammad as the system of record for tickets and customer communication
2) n8n automations for intake normalization, classification, draft replies, and incident promotion
3) Uptime Kuma for monitoring checks and a minimal public status page

AI is optional and used only as an agent-assist layer (summary, routing suggestion, draft reply). Final actions remain human-approved.

## What this demonstrates
- incident
- SLA
- ownership
- security guardrails

## Quick start (conceptual)
- Deploy Zammad using the official Docker Compose guidance (see `zammad/README.md`)
- Deploy n8n for workflows and integrations (see `docs/WORKFLOWS_N8N.md`)
- Deploy Uptime Kuma and configure status page (see `uptime-kuma/README.md`)
- Apply the incident and SLA policy described in `docs/INCIDENT_PROCESS.md` and `docs/SLA_POLICY.md`

## What to review
- `docs/ARCHITECTURE.md` for system boundaries and data flow
- `docs/SLA_POLICY.md` for B2B response targets and rules
- `docs/INCIDENT_PROCESS.md` for severity, roles, and comms templates
- `docs/WORKFLOWS_N8N.md` for the automation specs
- `docs/RUNBOOKS.md` for operational handling and failure modes
- `security/THREAT_NOTES.md` for safeguards (loops, attachments, abuse, audit)

## Status
Blueprint v0.1. Designed to be implemented incrementally and kept maintainable.
