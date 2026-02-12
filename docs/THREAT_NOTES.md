# Security and Abuse Notes (v0.1)

## Email intake abuse
- Use allowlist for trusted customer domains where possible
- Detect and block auto-reply patterns
- Rate limit repeated subjects from unknown senders
- Prevent loops where outgoing replies create new inbound tickets

## Attachments
- Default to quarantining or removing attachments
- Provide secure upload alternative for logs/screenshots
- Flag tickets that may contain sensitive data

## Auditability
- Ensure every automation action leaves an internal note with rule name and decision path
- Keep manual triage as a guaranteed fallback
- Avoid silent auto-closures without linkage to a primary ticket or incident

## Data minimization
- Store only what is required for support and incident handling
- Avoid copying secrets or credentials from emails into tickets
