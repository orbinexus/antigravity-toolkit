---
name: homelab-docker-architect
description: Configures, deploys, and orchestrates self-hosted private cloud services, media servers, VPNs, and homelab infrastructure using production-grade Docker Compose and networking configs.
---

# HomeLab & Self-Hosted Docker Architect

This skill provides turnkey deployment templates, secure networking architectures, and persistent storage configurations for self-hosted home servers, mini-PCs, and private cloud nodes.

## 1. Production Docker Compose Standards

1. **Volume Persistence & Permission Isolation**:
   - Explicitly define named volumes or host directory mounts with standard `PUID`/`PGID` variables to prevent permission lockouts.
   - Separate persistent state from transient application containers.
2. **Reverse Proxy & TLS Termination**:
   - Standardize automated SSL certificate acquisition via Traefik, Caddy, or Nginx Proxy Manager with Let's Encrypt DNS challenges.
   - Restrict administrative dashboards (Portainer, database GUIs) to private internal networks.
3. **Container Hardening**:
   - Set resource constraints (`cpus`, `memory`), healthchecks, and `restart: unless-stopped` policies.
   - Avoid `privileged: true` unless strictly required for hardware pass-through (e.g. QuickSync transcoding on Plex/Jellyfin).

## 2. Essential Self-Hosted Stacks
- **Network & Privacy**: Pi-hole / AdGuard Home, WireGuard / Tailscale mesh VPN, Cloudflare Tunnels.
- **Data & Storage**: Nextcloud, Vaultwarden (Bitwarden password manager), Photoprism / Immich.
- **Monitoring & Automation**: Prometheus, Grafana, Portainer, Uptime Kuma.
