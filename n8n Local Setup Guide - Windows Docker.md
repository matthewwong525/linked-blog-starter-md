# n8n Local Setup Guide - Windows Docker

## Prerequisites

Before starting, ensure you have the following installed on your Windows machine:

1. **Docker Desktop for Windows**
   - Download from: https://www.docker.com/products/docker-desktop
   - Requires Windows 10/11 Pro, Enterprise, or Education (64-bit)
   - Alternatively, Windows 10/11 Home with WSL 2 backend

2. **Git** (optional, but recommended)
   - Download from: https://git-scm.com/download/win

## Step-by-Step Installation Guide

### Step 1: Install Docker Desktop

1. Download Docker Desktop from the official website
2. Run the installer as Administrator
3. Follow the installation wizard
4. Restart your computer when prompted
5. Launch Docker Desktop and complete the initial setup
6. Verify installation by opening Command Prompt or PowerShell and running:
   ```cmd
   docker --version
   ```

### Step 2: Create Project Directory

1. Open Command Prompt or PowerShell as Administrator
2. Create a directory for your n8n setup:
   ```cmd
   mkdir C:\n8n-local
   cd C:\n8n-local
   ```

### Step 3: Method 1 - Simple Docker Run Command

Run n8n with a simple Docker command:

```cmd
docker run -it --rm --name n8n -p 5678:5678 -v C:\n8n-local\.n8n:/home/node/.n8n n8nio/n8n
```

**Command explanation:**
- `-it`: Interactive terminal
- `--rm`: Remove container when stopped
- `--name n8n`: Name the container "n8n"
- `-p 5678:5678`: Map port 5678 (host:container)
- `-v C:\n8n-local\.n8n:/home/node/.n8n`: Mount volume for data persistence
- `n8nio/n8n`: Official n8n Docker image

### Step 4: Method 2 - Using Docker Compose (Recommended)

Create a `docker-compose.yml` file in your `C:\n8n-local` directory:

```yaml
version: '3.8'

services:
  n8n:
    image: n8nio/n8n
    container_name: n8n
    restart: unless-stopped
    ports:
      - "5678:5678"
    environment:
      - N8N_BASIC_AUTH_ACTIVE=true
      - N8N_BASIC_AUTH_USER=admin
      - N8N_BASIC_AUTH_PASSWORD=your_secure_password_here
      - N8N_HOST=localhost
      - N8N_PORT=5678
      - N8N_PROTOCOL=http
      - WEBHOOK_URL=http://localhost:5678/
    volumes:
      - ./n8n-data:/home/node/.n8n
```

Run the setup using Docker Compose:

```cmd
cd C:\n8n-local
docker-compose up -d
```

### Step 5: Access n8n

1. Open your web browser
2. Navigate to: `http://localhost:5678`
3. If using basic auth (Method 2), enter:
   - Username: `admin`
   - Password: `your_secure_password_here`

### Step 6: Create Your First Workflow

1. Click "Add first step" or the "+" button
2. Choose a trigger node (e.g., "Schedule Trigger" for time-based workflows)
3. Add action nodes by clicking the "+" button after your trigger
4. Configure each node according to your needs
5. Click "Save" to save your workflow
6. Click "Execute Workflow" to test it

## Useful Docker Commands

### Managing the n8n Container

```cmd
# Start n8n (if using docker-compose)
docker-compose up -d

# Stop n8n
docker-compose down

# View logs
docker-compose logs -f n8n

# Restart n8n
docker-compose restart n8n

# Update n8n to latest version
docker-compose pull
docker-compose up -d
```

### Alternative Docker Commands (if not using docker-compose)

```cmd
# Stop the container
docker stop n8n

# Start the container
docker start n8n

# View logs
docker logs n8n

# Remove container
docker rm n8n
```

## Advanced Configuration

### Environment Variables

You can customize n8n behavior by adding environment variables to your `docker-compose.yml`:

```yaml
environment:
  - N8N_BASIC_AUTH_ACTIVE=true
  - N8N_BASIC_AUTH_USER=admin
  - N8N_BASIC_AUTH_PASSWORD=your_password
  - N8N_ENCRYPTION_KEY=your_encryption_key
  - EXECUTIONS_PROCESS=own
  - N8N_METRICS=true
  - N8N_LOG_LEVEL=info
```

### Persistent Data

Your workflows and credentials are stored in the mounted volume:
- **Docker run method**: `C:\n8n-local\.n8n`
- **Docker compose method**: `C:\n8n-local\n8n-data`

## Troubleshooting

### Common Issues

1. **Port 5678 already in use**
   ```cmd
   # Check what's using the port
   netstat -ano | findstr :5678
   
   # Change port in docker-compose.yml
   ports:
     - "5679:5678"  # Use port 5679 instead
   ```

2. **Docker Desktop not running**
   - Start Docker Desktop from Start Menu
   - Wait for Docker to fully initialize

3. **Permission issues with volumes**
   - Run Command Prompt/PowerShell as Administrator
   - Ensure Docker Desktop has access to C: drive

4. **Container won't start**
   ```cmd
   # Check container status
   docker ps -a
   
   # View detailed logs
   docker logs n8n
   ```

### Getting Help

- **n8n Documentation**: https://docs.n8n.io/
- **n8n Community Forum**: https://community.n8n.io/
- **Docker Documentation**: https://docs.docker.com/

## Security Notes

- Change default passwords before exposing to network
- Consider using HTTPS in production environments
- Regularly backup your n8n data directory
- Keep Docker and n8n images updated

---

*Guide created: September 15, 2025*
*Last updated: September 15, 2025*
