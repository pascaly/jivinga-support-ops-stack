# n8n Workflow Specs (v0.1)

Workflows are described at specification level. Production credentials and endpoints are not included.

## Workflow A: Email intake normalization (Zammad ticket created)
Trigger:
- Zammad webhook on ticket creation (or mailbox trigger if used)

Steps:
- Extract metadata (sender, subject, thread key, timestamps)
- Normalize subject (strip RE/FW, collapse whitespace)
- Detect customer org from domain mapping (fallback unknown)
- Add internal note with extracted metadata (sanitized)
- If subject matches outage keywords, set tag incident-suspect

Fallback:
- If parsing fails, route to Manual Triage queue

## Workflow B: Deduplication guard
Trigger:
- Ticket created with incident-suspect tag

Steps:
- Compute a thread key (message-id, in-reply-to, normalized subject key)
- Search recent open tickets with same key
- If found:
  - link as duplicate
  - add internal note
  - optionally close duplicate as "Duplicate"

## Workflow C: Severity suggestion (agent assist)
Trigger:
- Ticket created or updated

Steps:
- Determine severity candidate using deterministic rules first
- Optional AI assist for summary and classification suggestion
- Write suggestion into internal note
- Do not auto-promote to S0/S1 without human approval

## Workflow D: Promote to Incident
Trigger:
- Support agent sets field "Promote to Incident" = true

Steps:
- Create Incident ticket (or incident type in Zammad, depending on setup)
- Link support ticket to incident
- Notify ops channel
- Prepare customer initial notice draft

## Workflow E: Status page update helper
Trigger:
- Incident state enters Mitigating / Resolved

Steps:
- Create a draft status page update text (human approval)
- Log the update in the incident timeline

## Workflow F: Resolution propagation
Trigger:
- Incident marked Resolved

Steps:
- Comment on linked customer tickets with resolution message template
- Move customer tickets to "Resolved" or request confirmation
