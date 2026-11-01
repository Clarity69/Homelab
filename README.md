<div align="center">

# Personal Homelab Infrastructures

[![OS - Ubuntu Server LTS](https://img.shields.io/badge/OS-Ubuntu_Server_LTS-E95420?style=for-the-badge&logo=ubuntu&logoColor=white)](https://ubuntu.com/server)
[![Docker Engine](https://img.shields.io/badge/Container-Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)](https://www.docker.com/)
[![Tailscale Enabled](https://img.shields.io/badge/Network-Tailscale-242424?style=for-the-badge&logo=tailscale&logoColor=white)](https://tailscale.com/)
[![Status - Active](https://img.shields.io/badge/Status-Operational-44CC11?style=for-the-badge)](https://github.com)

*Repositori terpusat untuk konfigurasi Docker Compose, arsitektur jaringan, dan panduan disaster recovery homelab.*

</div>

---

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
|                  HOMELAB SERVER (Ubuntu Server LTS)                   |
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
- CPU: Intel® Core™ i3-2120 (2 Cores, 4 Threads @ 3.30 GHz)

- RAM: 8 GB DDR3

- Storage: 256 GB HDD

- OS: Ubuntu Server LTS (x86_64)

## Navigation/Documentation
- docs/recovery-protocol.md — Panduan penanganan insiden darurat, reset password admin (Homarr, Portainer, Beszel Hub), dan perbaikan database lock

- docker/ — Direktori berkas docker-compose.yml untuk setiap stack layanan