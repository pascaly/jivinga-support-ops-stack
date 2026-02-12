# Runbooks (v0.1)

## Runbook 1: Zammad intake is down
Symptoms:
- inbound emails not creating tickets
- support inbox is silent

Actions:
1) Confirm email provider is delivering messages.
2) Check Zammad container/service health.
3) Check DB connectivity and storage pressure.
4) If recovery is slow, switch to temporary fallback:
   - dedicate a mailbox folder for manual triage
   - log all urgent reports into a single manual ticket once Zammad recovers
5) After recovery:
   - reconcile missed emails into tickets
   - note the gap and create a follow-up action

## Runbook 2: Automation malfunction (n8n)
Symptoms:
- misrouted tickets
- duplicate tickets created
- incorrect severity classification

Actions:
1) Disable the specific workflow (do not stop all automation unless necessary).
2) Route tickets to manual triage queue.
3) Review the last 20 executions for the workflow.
4) Fix rule logic and re-enable.
5) Retroactively correct:
   - merge duplicates
   - relabel severity
   - link tickets to incidents if needed

## Runbook 3: Customer reports outage (possible incident)
Actions:
1) Mark ticket as incident-suspect and prioritize triage.
2) Check monitoring signals (Uptime Kuma) and internal indicators.
3) If user impact is confirmed:
   - create an Incident
   - link the customer ticket to the Incident
   - assign Incident Owner
   - send initial customer notice
4) If uncertain:
   - keep in manual triage
   - request exact timestamps, error message, and scope from customer
5) Close loop:
   - once resolved, update the customer ticket and confirm recovery

## Postmortem (minimal template)
- Summary: what happened in 3 to 5 sentences
- Impact: who was affected, duration, symptoms
- Timeline (UTC): key events
- Root cause: primary cause and contributing factors
- Corrective actions: action, owner, due date
