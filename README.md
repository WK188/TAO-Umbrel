![umbrelOS](https://github.com/user-attachments/assets/cabf8af7-51ce-45df-ad3a-a664cc91c610)

# umbrelOS (Unofficial Docker Image)

> ⚠️ **Important Notice: This is an unofficial Docker image!**  
> This project is a modified version of **umbrelOS v1.5.0**, designed to run directly in a Docker container instead of as a host operating system.  
> **It is not endorsed or supported by the Umbrel official team. Use at your own risk.**  
>
> Official Umbrel website: <https://umbrel.com>  
> GitHub Repository: <https://github.com/WK188/TAO-Umbrel>

---

# ⭐ umbrelOS  
## A beautiful self-hosted home server OS

Umbrel's vision is to let everyone enjoy the convenience of the cloud while maintaining full control over their data.

With Umbrel, you can easily deploy apps and services on a small home server, creating your own private cloud.

---

# 🚀 How to run this Docker image

This is a **containerized version of umbrelOS**. No need for bare-metal installation or virtual machines—just run it with Docker.

---

## 1. Pull the image

```bash
docker pull tao9317/tao-umbrel:latest
```

---

## 2. Run using Docker Compose (recommended)

> ❗ **Important:**  
> UmbrelOS manages other Docker containers, so you must mount the host Docker socket and enable `pid: host`.

Create a `docker-compose.yml`:

```yaml
services:
  umbrel:
    image: tao9317/tao-umbrel:latest
    container_name: umbrel
    pid: host
    ports:
      - "80:80"
    volumes:
      # Persist Umbrel data
      - ./umbrel:/data
      # Allow Umbrel to control host Docker
      - /var/run/docker.sock:/var/run/docker.sock
    restart: always
    stop_grace_period: 1m
```

Start the container:

```bash
docker-compose up -d
```

---

## 3. Access UmbrelOS

Wait a few minutes for initialization, then visit:

```
http://<YOUR_HOST_IP>:80
```

to access the UmbrelOS web interface.

---

# ⚙️ Optional Environment Variables

| Variable | Default | Description |
|---------|--------|------|
| `TZ` | `Etc/UTC` | Container timezone, e.g., `Asia/Shanghai` |
| `UMBREL_DEBUG` | `false` | Enable debug logs for troubleshooting |
| `UMBREL_DATA_DIR` | `/data` | Mounted Umbrel data directory |
| `UMBREL_PORT` | `80` | Web UI port |

> Add more variables if needed.

---



# 📜 License

UmbrelOS is licensed under **PolyForm Noncommercial 1.0.0**.

**TL;DR:**

- Free for **personal** and **non-commercial** use, modification, and redistribution.  
- Commercial use is prohibited.  
- This Docker image is subject to the same license.

---

Thanks for using! Feedback and suggestions are welcome! 🔥
