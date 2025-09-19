# Setup Steps
1. Prepare the Traefik `docker-compose.yml` File
```yml
version: '3.8'

services:
  traefik:
    image: traefik:v2.11  # Using a recent version of Traefik
    container_name: traefik
    restart: unless-stopped
    ports:
      - "80:80"    # The HTTP port
      - "443:443"  # The HTTPS port
    volumes:
      - /var/run/docker.sock:/var/run/docker.sock:ro  # To monitor Docker containers
      - ./acme.json:/acme.json                        # To store Let's Encrypt certificates
    command:
      # Entrypoints for HTTP and HTTPS traffic
      - --entrypoints.web.address=:80
      - --entrypoints.websecure.address=:443
      # Enable Docker provider and expose containers
      - --providers.docker
      - --providers.docker.exposedbydefault=false
      # Let's Encrypt (ACME) setup
      - --certificatesresolvers.letsencrypt.acme.tlschallenge=true
      - --certificatesresolvers.letsencrypt.acme.email=your-email@example.com  # 📧 Replace with your email
      # Disable the dashboard for security
      - --api=false
      - --api.dashboard=false
    networks:
      - web

networks:
  web:
    external: true
```

2. Create a Shared Network and `acme.json`
	1. Create a Docker network named `web` for your services:
	```bash
	docker network create web
	```
	2. Create the `acme.json` file where Traefik will store your SSL certificates. Set its permissions to be read-only for security.
```bash
mkdir traefik
cd traefik
touch acme.json
chmod 600 acme.json
```

1. Modify the n8n `docker-compose.yml`
	1. **Remove the `ports` section** from the n8n service. Traefik will handle external access, so `n8n` only needs to be accessible from within the `web` network.
	2. **Add a `networks` section** to connect n8n to the `web` network.
	3. **Add `labels`** to configure Traefik routing.
```yml
services:
  n8n:
    image: n8nio/n8n
    user: "1000:1000"
    container_name: n8n
    restart: unless-stopped
    # The ports section is removed
    volumes:
      - n8n_data:/home/node/.n8n
    environment:
      - N8N_SECURE_COOKIE=true # Use true for HTTPS
      - N8N_HOST=n8n.yourdomain.com # 🌐 Replace with your domain
      - N8N_PROTOCOL=https
      - WEBHOOK_URL=https://n8n.yourdomain.com/
    networks:
      - web # Connect to the Traefik network
    labels:
      - "traefik.enable=true"
      - "traefik.http.routers.n8n.rule=Host(`n8n.yourdomain.com`)" # 🌐 Match your domain
      - "traefik.http.routers.n8n.entrypoints=websecure"
      - "traefik.http.routers.n8n.tls.certresolver=letsencrypt"
      - "traefik.http.services.n8n.loadbalancer.server.port=5678"

volumes:
  n8n_data:

networks:
  web:
    external: true
```

4. Launch the Services
	1. In your `traefik` directory, run `docker-compose up -d`. This will start Traefik.
	2. In your `n8n` directory, run `docker-compose up -d`. This will start n8n.