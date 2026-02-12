# Component ownership (v0.1)

This table defines primary ownership for routing and incident coordination.
Ownership is about accountability, not exclusive execution.

Legend:
- Primary: accountable owner for triage and coordination
- Secondary: backup and escalation path

| Component | Scope | Primary owner | Secondary owner | Typical tickets | Notes |
|---|---|---|---|---|---|
| Check-in | QR entry, session start, gating entry | Platform / App | Ops | “Can’t check in”, invalid token, session loops | High impact at venues |
| Program | timelines, schedule visibility | Platform / App | Ops | missing items, wrong time visibility | Time windows matter |
| Bulletin | announcements, publish windows | Platform / App | Ops | delayed updates, visibility issues | Background resume risk |
| Upload | picture upload, storage paths | Platform / App | Ops | upload fails, wrong path, permissions | Watch for size limits |
| Auth | login, tokens, session validity | Platform / App | Security/ops | 401s, session confusion | Sensitive area |
| Admin / Venue | admin UI, venue settings, shortlinks | Platform / App | Ops | config mistakes, access issues | Audit changes |
| API / Backend | servlets, DB operations | Backend | Ops | 500s, data issues | Include DB health |
| Database | MariaDB health, schema, backups | Ops | Backend | slow queries, locks, errors | Ensure recovery steps |
| Infrastructure | DNS, TLS, hosting, reverse proxy | Ops | Platform | downtime, cert renewals | Link to status checks |
| Support process | Zammad groups, SLA, macros | Ops / Support lead | Platform | routing, duplicates, templates | Keep it simple |
