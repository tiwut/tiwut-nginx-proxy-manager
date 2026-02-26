# Tiwut Nginx Proxy Manager (NPM)

This repository contains a custom-built Docker image of the **Nginx Proxy Manager**. It is designed for easy deployment across multiple environments with persistent storage for configurations and SSL certificates.

### Key Features:
* **Secure Reverse Proxy:** Easily manage forwarding to your internal services.
* **Free SSL:** Integrated Let's Encrypt support.
* **Lightweight:** Based on the official NPM image for maximum stability.

### Deployment (Docker Compose)
To use this image on your server, create a `docker-compose.yml` file and paste the following content:

```yaml
version: '3.8'
services:
  nginx-proxy-manager:
    image: tiwutdev/tiwut-nginx-proxy-manager:latest
    container_name: nginx-proxy-manager
    restart: unless-stopped
    ports:
      - '80:80'    # HTTP Traffic
      - '81:81'    # Admin Web Interface
      - '443:443'  # HTTPS Traffic
    volumes:
      - ./data:/data
      - ./letsencrypt:/etc/letsencrypt
