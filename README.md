# portfolio

Source code for my personal engineering portfolio, self-hosted via Nginx and exposed via Cloudflare Tunnels.

## Architecture & Deployment

* **Web Server:** Nginx (`nginx:alpine`) serving static assets read-only from `/usr/share/nginx/html`.
* **Ingress:** Cloudflare Tunnel (`cloudflared`) routing external HTTPS traffic to the internal container network without open host ports.
* **Infrastructure:** Deployed on `lord-of-the-pings`. See the [homelab repository](https://github.com/AurelSto/homelab) for Docker Compose configurations and stack architecture.
