# Deployment (Linux, production v0.1)

This folder documents a real-world deployment approach for:
- Zammad (system of record for Support + Incidents) on support.jivinga.com
- n8n (automation) on automation.jivinga.com (recommended restricted access)
- Uptime Kuma (monitoring + status page) on status.jivinga.com

No secrets are committed. Use `.env` files locally and a secure secret store.

## 1) DNS
Create A/AAAA records:
- support.jivinga.com -> <server_ip>
- status.jivinga.com -> <server_ip>
- automation.jivinga.com -> <server_ip>

## 2) Host prerequisites
- Linux host with Docker + Docker Compose plugin
- Firewall: allow 80/443, restrict admin ports
- Automatic security updates (optional but recommended)
- Backups for volumes and DB

## 3) Reverse proxy (TLS termination)
Use Nginx (or Caddy) to:
- terminate TLS (Let's Encrypt)
- route each subdomain to the correct internal service port

## 4) Zammad (support.jivinga.com)
Deploy using the official Zammad Docker Compose documentation and scenarios.
Zammad is the single system of record for both Support and Incidents.

Post-deploy checklist (in Zammad):
- Create groups: "Jivinga Support", "Jivinga Incidents"
- Add minimal fields (Customer Org, Component, Environment, Severity)
- Add macros for incident comms (initial update, progress update, resolved notice)

## 5) n8n (automation.jivinga.com)
Deploy with Docker Compose using official n8n guidance.
Security:
- enforce auth
- restrict access (IP allowlist or VPN) if possible
- store credentials in n8n credential store, not in git

## 6) Uptime Kuma (status.jivinga.com)
Deploy with Docker.
Expose only the status page publicly. Protect the admin UI.

## 7) Backups
Back up:
- Zammad volumes and database
- n8n workflow data
- Uptime Kuma data volume

See `backup/backup.sh` and `backup/restore.md`.

## 8) Updates
- Prefer small, scheduled updates
- Always snapshot volumes before upgrading
- Validate mail channel and outbound delivery after upgrades
