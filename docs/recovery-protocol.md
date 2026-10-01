# Homelab Emergency Recovery Protocol

Dokumen ini berisi prosedur pemulihan kredensial darurat jika terjadi kegagalan login, database lock, atau lupa password pada layanan yang di-host.

---

## 1. Beszel Hub (Monitoring)
**Problem:** Login attempt failed / SQLite database lock / panic error.
```bash
# Opsi 1: Reset/Update password superuser tanpa menghapus data
sudo docker exec -it beszel-hub /beszel superuser upsert admin@homelab.local PasswordBaru123!

# Opsi 2: Jika database SQLite corrupt (Hard Reset)
cd ~/Homelab/docker/beszel
sudo docker compose down
sudo rm -rf ./data/*
sudo docker compose up -d
sudo docker exec -it beszel-hub /beszel superuser create admin@homelab.local PasswordBaru123!
```

## 2. Homarr(Dashboard)

**Login attemp failed**
```bash
cd ~/Homelab/docker/homarr
sudo docker compose down
sudo mv ./data/db/db.sqlite ./data/db/db.sqlite.bak
sudo docker compose up -d
```

## Portainer

**Forget Password**
```bash
sudo docker stop portainer
sudo docker run --rm -v portainer_data:/data portainer/helper-reset-password
sudo docker start portainer
```