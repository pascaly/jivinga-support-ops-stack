# Incident Process (v0.1)

## Purpose
Provide a lightweight but serious incident lifecycle for Jivinga, including customer communication.

## Severity (incident side)
- S0: critical outage or severe security risk, widespread impact
- S1: major degradation, many customers impacted
- S2: partial impact or limited customer set
- S3: minor incident, low impact

## Roles
- Incident Owner: accountable for coordination and decisions
- Incident Scribe: captures timeline and updates (can be same person in v0.1)
- Support Lead: customer-facing triage and coordination with incident owner

## Lifecycle states
1) Intake
2) Acknowledged
3) Mitigating
4) Monitoring
5) Resolved
6) Closed

## State rules
- Acknowledged requires an assigned Incident Owner and severity.
- Mitigating requires regular internal updates (for example every 15 to 30 minutes for S0/S1).
- Resolved requires minimal closure data (impact window and follow-ups).

## Customer communication (email-only, v0.1)
For S0/S1:
- Initial notice as soon as confirmed user impact
- Updates with a next checkpoint time
- Resolution notice + next steps

For S2/S3:
- Inform affected customers as appropriate
- Prefer targeted emails over broad broadcasts

## Customer update templates

### Initial notice
Subject: [Jivinga] Service disruption update
Body:
- What happened: <one line>
- Impact: <who/what is affected>
- Current action: <what we are doing now>
- Next update: <time>

### Progress update
Subject: [Jivinga] Service disruption update (progress)
Body:
- Current status: <one line>
- Impact: <still affected / improving>
- Next update: <time>

### Resolved notice
Subject: [Jivinga] Service restored
Body:
- Status: service restored
- Impact window: <start time> to <end time>
- Follow-up: we will share a short summary if needed
- Contact: reply to this email for any remaining issues

## Postmortem trigger
- Required for S0 and S1
- Optional for S2 when systemic
- Minimal template is in `docs/RUNBOOKS.md`
