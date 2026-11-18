# portfolio

Source code for my personal engineering portfolio at aurels.ro: a static site self-hosted on my home server and exposed through a Cloudflare Tunnel, with no open inbound ports.

## Architecture & Deployment

Visitor → Cloudflare (TLS) → Cloudflare Tunnel → cloudflared → Caddy → Nginx (static files)


* **Web Server:** Nginx (`nginx:alpine`) serves this repository's files read-only from /usr/share/nginx/html.
* **Reverse Proxy & TLS:** CCaddy forwards plain HTTP to Nginx on a private Docker network (web_net). It publishes no host ports; TLS is terminated at Cloudflare.
* **Ingress:** cloudflared makes an outbound connection to Cloudflare and routes the public hostname to Caddy, so the router has no port forwards.
* **Infrastructure:** runs on lord-of-the-pings. Compose files and the full topology are in the [homelab repository](https://github.com/AurelSto/homelab)

## Updating the site

Edit the files in html/ on the server (or pull this repository there). Nginx serves them directly, so no rebuild or restart is needed.

## Credits and license

Based on a free template from HTML5 UP, licensed under Creative Commons Attribution 3.0. See LICENSE.txt. Template assets under assets/ are third-party code and are excluded from language statistics via .gitattributes.
