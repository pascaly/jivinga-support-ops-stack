# SLA Policy (B2B, v0.1)

This is a pragmatic early-stage SLA policy. It prioritizes predictable response and ownership over complex tooling.

## Definitions
- First response: first human response to the customer (not an auto-ack).
- Update: meaningful progress update with next checkpoint time.
- Waiting for Customer: pauses SLA timers.

## Severity (support side)
- S1: major impact, core functionality blocked for the customer
- S2: partial impact or workaround exists
- S3: minor issue, how-to, small defect

## Targets (business hours)
S1:
- First response: 1 hour
- Update cadence: every 4 hours until stable workaround or resolution path

S2:
- First response: 4 hours
- Update cadence: 1 business day

S3:
- First response: 1 business day
- Update cadence: best effort

## Rules
- Every ticket must have an owner after triage.
- If a ticket is suspected to be a platform-wide issue, it must be promoted to an Incident (see Incident Process).
- Waiting for Customer pauses SLA.
- Duplicate tickets should be linked to a primary ticket or primary incident.
