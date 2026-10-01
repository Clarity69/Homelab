# My homelab Documentation

## Hosted Services & Port Allocations

| Service | Category | Host Port | Description | Status |
| :--- | :--- | :---: | :--- | :---: |
| **Homarr** | Dashboard | `4000` | Centralized navigation dashboard | 🟢 Active |
| **Nextcloud** | Cloud Storage | `8080` | Personal cloud & file synchronization | 🟢 Active |
| **Beszel Hub** | Monitoring | `8090` | Lightweight server resource tracker | 🟢 Active |
| **Uptime Kuma** | Monitoring | `3001` | Service uptime & status monitoring | 🟢 Active |
| **Portainer** | Management | `8000` / `9443` | Docker container management GUI | 🟢 Active |
| **Laravel Kanban** | Productivity | `8888` | Self-hosted task & project management board | 🟢 Active |
| **Kanban MySQL** | Database | `3306` | Database engine for Kanban application | 🟢 Active |
| **Tailscale** | Networking | Native | Encrypted mesh VPN for remote administration | 🟢 Active |
| **Cloudflare Tunnel** | Networking | Outbound | Zero-Trust secure tunnel for public endpoints | 🟢 Active |

---

## Network & Infrastructure Architecture

```text
+-----------------------------------------------------------------------+
|                            CLIENT DEVICES                             |
|                  (Laptop / Smartphone / Workstation)                  |
+-----------------------------------------------------------------------+
                                   |
       +---------------------------+---------------------------+
       |                           |                           |
(Local Network)             (Tailscale Mesh)            (Public WAN)
192.168.1.x / LAN           100.x.y.z / VPN             Cloudflare Tunnel
       |                           |                           |
       v                           v                           v
+---------------+           +---------------+           +---------------+
| LOCAL ROUTER  |           | TAILSCALE VPN |           | CLOUDFLARE    |
+---------------+           +---------------+           +---------------+
       |                           |                           |
       +---------------------------+---------------------------+
                                   |
                                   v
+-----------------------------------------------------------------------+
|                     HOMELAB SERVER (Arch Linux)                       |
|                                                                       |
|  +-----------------------------------------------------------------+  |
|  |                   DOCKER CONTAINER ENVIRONMENT                  |  |
|  |                                                                 |  |
|  |   [Dashboard]      ---> Homarr (Port 4000)                      |  |
|  |   [Cloud Storage]  ---> Nextcloud (Port 8080)                   |  |
|  |   [Monitoring]     ---> Beszel Hub (Port 8090)                  |  |
|  |   [Uptime]         ---> Uptime Kuma (Port 3001)                 |  |
|  |   [Management]     ---> Portainer (Port 8000/9443)              |  |
|  |   [Productivity]   ---> Kanban App (Nginx: 8888, DB: 3306)      |  |
|  |   [Ingress]        ---> Cloudflare Tunnel & Tailscale           |  |
|  +-----------------------------------------------------------------+  |
+-----------------------------------------------------------------------+
```
## Specification
- CPU: i3 2120
- RAM   : 8 GB/DDR 3
- Storage   : 256 GB 
- OS:  Ubuntu Server LTS
