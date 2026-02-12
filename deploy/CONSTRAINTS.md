# Deployment constraints (legacy host)

The current legacy host (CentOS 7, restricted virtualization) cannot run Docker containers.
Symptoms:
- Any container fails at runtime with: "error mounting proc ... permission denied"
- FUSE is unavailable (/dev/fuse missing; modprobe fuse not permitted)

Implication:
- The support stack (Uptime Kuma, Zammad, n8n) must be deployed on a modern VM (KVM) or a host with proper container support.

Recommended approach:
- Provision a small modern VM (Debian 12 / Ubuntu 22.04+ / Rocky 9)
- Deploy Kuma first on status.jivinga.com
- Deploy Zammad next on support.jivinga.com
- Keep the legacy host unchanged until full migration is executed
