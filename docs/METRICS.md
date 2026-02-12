# Metrics (v0.1)

This document defines a minimal, review-friendly set of operational metrics for a B2B email-only support model with incidents tracked in Zammad.

Principles:
- Prefer a small set of metrics that drive action.
- Track trends, not vanity numbers.
- Use consistent time windows (weekly and monthly).

## Support metrics

### Ticket aging
Purpose: prevent silent backlog growth and forgotten customers.
- Aging buckets (open tickets):
  - 0–1 business day
  - 2–3 business days
  - 4–7 business days
  - >7 business days

Action triggers:
- Any ticket >7 business days must have an owner and a next step.
- Weekly review of >4 business days bucket.

### First Response Time (FRT)
Definition: time from ticket creation to first human response (excluding auto-ack).
Track:
- Median and p90, per severity (S1/S2/S3).
Use:
- Validates that intake and triage are functioning.

### Update Time (UT)
Definition: time between meaningful customer-facing updates while ticket remains active.
Track:
- Median and p90, per severity.
Use:
- Prevents “ticket stagnation.”

### Reopen rate
Definition: percentage of tickets reopened after being marked resolved/closed.
Use:
- Signals weak resolution quality or communication gaps.

### Noise rate (support)
Definition: percentage of inbound tickets that are:
- duplicates
- misrouted
- invalid / spam / auto-replies
Use:
- Measures how well the system filters and deduplicates intake.

## Incident metrics (tracked in Zammad as Incident tickets)

### MTTA (Mean Time To Acknowledge)
Definition: time from incident creation (or first detection) to “Acknowledged” with an assigned Incident Owner.

Track:
- Median and p90 for S0/S1 incidents.

Target examples:
- S0: acknowledge within 5–10 minutes (operational goal)
- S1: acknowledge within 15–30 minutes

### MTTM (Mean Time To Mitigate)
Definition: time from incident acknowledged to first effective mitigation (impact reduced or stabilized).

Track:
- Median and p90 for S0/S1 incidents.

### MTTR (Mean Time To Resolve)
Definition: time from incident creation to “Resolved” (impact ended).

Track:
- Median and p90, per severity.

### Incident update cadence adherence
Definition: percentage of incidents where the team posted updates at the intended cadence.
Use:
- Reinforces disciplined communication and coordination.

### Incident dedup ratio
Definition: number of customer tickets linked to a single incident (and how many duplicates were merged/closed).
Use:
- Measures consolidation quality and reduces fragmented response.

## Reporting cadence (v0.1)
Weekly:
- Ticket aging buckets
- FRT and UT by severity
- Open incidents and status

Monthly:
- MTTA / MTTM / MTTR trends
- Noise rate trend
- Top components by ticket and incident count
- Postmortem follow-up completion rate (S0/S1)
