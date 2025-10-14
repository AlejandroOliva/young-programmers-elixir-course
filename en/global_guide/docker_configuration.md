# 🐳 Docker/Podman Configuration

## 🎯 Introduction

Docker (or Podman) provides a simple and portable way to run Elixir and Livebook without needing to install dependencies on your system. This is an excellent option if:

- You want an isolated and reproducible environment
- You have difficulties with local installation
- You want to try the course before installing it permanently
- You work on multiple computers

## 📋 Prerequisites

- Computer with Windows, macOS, or Linux
- At least 4 GB of available RAM
- 2-3 GB of free disk space
- Internet connection (only for initial setup)

## 🔧 Installing Docker/Podman

### Option A: Docker Desktop (Recommended for beginners)

#### Windows and macOS

1. **Download Docker Desktop:**
   - Go to https://www.docker.com/products/docker-desktop
   - Download the version for your operating system
   - Approximate size: 400-500 MB

2. **Install Docker Desktop:**
   - Run the downloaded installer
   - Follow the wizard instructions
   - Restart the computer if requested

3. **Start Docker Desktop:**
   - Open the Docker Desktop application
   - Accept the terms of service
   - Wait for Docker to start completely (green icon in system tray)

4. **Verify the installation:**
   - Open a terminal/PowerShell
   - Run:
     ```bash
     docker --version
     ```
   - You should see something like: `Docker version 24.0.x`

#### Linux

```bash
# Ubuntu/Debian
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
sudo usermod -aG docker $USER
# Log out and log back in to apply changes

# Fedora
sudo dnf install docker-ce docker-ce-cli containerd.io
sudo systemctl start docker
sudo usermod -aG docker $USER

# Arch Linux
sudo pacman -S docker
sudo systemctl start docker
sudo usermod -aG docker $USER
```

### Option B: Podman (Open-source alternative)

Podman is a Docker-compatible alternative, daemonless and with better security.

#### Linux

```bash
# Ubuntu/Debian
sudo apt-get install podman

# Fedora (comes pre-installed in recent versions)
sudo dnf install podman

# Arch Linux
sudo pacman -S podman
```

#### macOS

```bash
brew install podman
podman machine init
podman machine start
```

#### Windows

1. Download from: https://github.com/containers/podman/releases
2. Install the `.msi` file
3. Open PowerShell and run:
   ```powershell
   podman machine init
   podman machine start
   ```

**Note:** In the rest of this guide, if you use Podman, simply replace `docker` with `podman` in all commands.

## 🚀 Livebook Configuration with Docker

### Method 1: Use the Official Livebook Image (Simpler)

#### Run Livebook

```bash
docker run -p 8080:8080 -p 8081:8081 --pull always \
  -v $(pwd):/data \
  livebook/livebook
```

**On Windows PowerShell:**
```powershell
docker run -p 8080:8080 -p 8081:8081 --pull always -v ${PWD}:/data livebook/livebook
```

**Parameter explanation:**
- `-p 8080:8080`: Exposes Livebook's port
- `-p 8081:8081`: Additional port for communication
- `--pull always`: Ensures you have the latest version
- `-v $(pwd):/data`: Mounts your current directory to save notebooks
- `livebook/livebook`: The official image

#### Access Livebook

1. After running the command, you'll see a message in the terminal
2. Look for a line like: `Access Livebook at http://localhost:8080/?token=...`
3. Copy that complete URL
4. Open it in your browser
5. You can now use Livebook!

#### Stop Livebook

- Press `Ctrl + C` in the terminal

### Method 2: Docker Compose (Recommended for frequent use)

#### Create configuration file

1. Create a folder for the course:
   ```bash
   mkdir ElixirKidsCourse
   cd ElixirKidsCourse
   ```

2. Create a file named `docker-compose.yml`:

```yaml
version: '3.8'

services:
  livebook:
    image: livebook/livebook:latest
    ports:
      - "8080:8080"
      - "8081:8081"
    environment:
      - LIVEBOOK_PASSWORD=elixirkids
      - LIVEBOOK_HOME=/data
    volumes:
      - ./notebooks:/data
    restart: unless-stopped
```

3. Create the notebooks folder:
   ```bash
   mkdir notebooks
   ```

#### Start Livebook

```bash
docker-compose up -d
```

The `-d` parameter runs Livebook in the background.

#### Access Livebook

1. Open your browser
2. Go to: http://localhost:8080
3. Enter the password: `elixirkids`
4. Ready to program!

#### Useful commands

```bash
# View logs
docker-compose logs -f

# Stop Livebook
docker-compose down

# Restart Livebook
docker-compose restart

# View status
docker-compose ps
```

## 🎨 Custom Configuration

### Change the port

If port 8080 is already in use, modify the `docker-compose.yml` file:

```yaml
ports:
  - "9090:8080"  # Change 9090 to your preferred port
  - "9091:8081"
```

Then access at: http://localhost:9090

### Configure memory

If Livebook needs more memory:

```yaml
services:
  livebook:
    # ... previous configuration ...
    deploy:
      resources:
        limits:
          memory: 2G
        reservations:
          memory: 1G
```

### Persist data

To ensure your notebooks aren't lost:

```yaml
volumes:
  - ./notebooks:/data  # Notebooks and files
  - livebook_deps:/root/.mix  # Elixir dependencies
  
volumes:
  livebook_deps:
```

## 🔍 Verification

### Test that it works

1. Access Livebook in your browser
2. Click on "New notebook"
3. Write in the first cell:
   ```elixir
   IO.puts("Docker works perfectly!")
   System.version()
   ```
4. Press "Evaluate" or `Ctrl+Enter`
5. You should see the message and the Elixir version

### Test Kino

In a new cell:

```elixir
Mix.install([
  {:kino, "~> 0.12.0"}
])

Kino.Input.text("What's your name?")
```

If you see an interactive text field, everything works correctly!

## 🛠️ Quick Start Script

### For Linux/macOS

Create a file `start-livebook.sh`:

```bash
#!/bin/bash

# Colors for output
GREEN='\033[0;32m'
BLUE='\033[0;34m'
NC='\033[0m' # No Color

echo -e "${BLUE}🚀 Starting Livebook...${NC}"

# Check if Docker is running
if ! docker info > /dev/null 2>&1; then
    echo "Error: Docker is not running. Please start Docker Desktop."
    exit 1
fi

# Create notebooks directory if it doesn't exist
mkdir -p notebooks

# Start Livebook
docker run -d \
  --name elixir-kids-livebook \
  -p 8080:8080 \
  -p 8081:8081 \
  -e LIVEBOOK_PASSWORD=elixirkids \
  -v $(pwd)/notebooks:/data \
  livebook/livebook:latest

echo -e "${GREEN}✅ Livebook started successfully${NC}"
echo -e "📱 Access at: ${BLUE}http://localhost:8080${NC}"
echo -e "🔑 Password: elixirkids"
echo ""
echo "To stop Livebook, run: docker stop elixir-kids-livebook"
```

Make it executable:
```bash
chmod +x start-livebook.sh
./start-livebook.sh
```

### For Windows

Create a file `start-livebook.bat`:

```batch
@echo off
echo Starting Livebook...

REM Check if Docker is running
docker info >nul 2>&1
if errorlevel 1 (
    echo Error: Docker is not running. Please start Docker Desktop.
    pause
    exit /b 1
)

REM Create notebooks directory
if not exist notebooks mkdir notebooks

REM Start Livebook
docker run -d ^
  --name elixir-kids-livebook ^
  -p 8080:8080 ^
  -p 8081:8081 ^
  -e LIVEBOOK_PASSWORD=elixirkids ^
  -v %cd%/notebooks:/data ^
  livebook/livebook:latest

echo Livebook started successfully
echo Access at: http://localhost:8080
echo Password: elixirkids
echo.
echo To stop Livebook, run: docker stop elixir-kids-livebook
pause
```

Run by double-clicking the file.

## 🔄 Updating

### Update Livebook image

```bash
docker pull livebook/livebook:latest
```

Or with docker-compose:
```bash
docker-compose pull
docker-compose up -d
```

## 🚧 Troubleshooting

### Docker Desktop won't start

**Problem:** Docker Desktop gets stuck loading.

**Solution:**
1. Restart the computer
2. Temporarily disable antivirus
3. On Windows, verify virtualization is enabled in BIOS

### Port 8080 already in use

**Problem:** Error "port is already allocated"

**Solution:**
```bash
# See what's using the port
# Linux/macOS
lsof -i :8080

# Windows
netstat -ano | findstr :8080

# Change port in docker-compose.yml or use:
docker run -p 9090:8080 ... livebook/livebook
```

### Can't access Livebook

**Problem:** Browser doesn't load localhost:8080

**Solution:**
1. Verify the container is running:
   ```bash
   docker ps
   ```
2. Check the logs:
   ```bash
   docker logs elixir-kids-livebook
   ```
3. Try accessing: http://127.0.0.1:8080

### Notebooks aren't being saved

**Problem:** When restarting Docker, notebooks disappear.

**Solution:**
Make sure to use the `-v` parameter:
```bash
-v $(pwd)/notebooks:/data
```

Verify the `notebooks` folder exists in your current directory.

### Error "Cannot connect to Docker daemon"

**Problem:** Docker doesn't respond.

**Solution:**
- **Linux:** `sudo systemctl start docker`
- **macOS/Windows:** Start Docker Desktop manually

### Livebook very slow

**Problem:** Performance is low.

**Solution:**
1. Assign more resources to Docker:
   - Docker Desktop → Settings → Resources
   - Increase CPU and memory (minimum 2 CPU, 4GB RAM)
2. Close other containers:
   ```bash
   docker ps
   docker stop <unnecessary-container>
   ```

## 💡 Advantages of using Docker

✅ **Isolation:** Doesn't interfere with other installations on your system

✅ **Portability:** Works the same on Windows, macOS, and Linux

✅ **Simplicity:** Doesn't require manually installing dependencies

✅ **Reproducibility:** Same environment for all students

✅ **Easy to clean:** Removing the container cleans everything

## ⚠️ Considerations

❗ **Performance:** Slightly slower than native installation

❗ **Resources:** Requires Docker Desktop running (uses memory)

❗ **Initial complexity:** Learning curve to understand Docker

❗ **Updates:** Must update image manually

## 📁 Recommended Organization

```
ElixirKidsCourse/
├── docker-compose.yml
├── start-livebook.sh (or .bat)
└── notebooks/
    ├── level_1/
    ├── level_2/
    ├── level_3/
    ├── my_projects/
    └── extra_exercises/
```

## 🔄 Notebook Backup

### Manual backup

```bash
# Copy all notebooks
cp -r notebooks notebooks-backup-$(date +%Y%m%d)
```

### Automatic backup

Add this to `docker-compose.yml`:

```yaml
services:
  livebook:
    # ... previous configuration ...
    volumes:
      - ./notebooks:/data
      - ./backups:/backups
```

## 📞 Next Steps

1. ✅ Verify Docker/Livebook works correctly
2. ✅ Create folder structure for notebooks
3. ✅ Download notebooks from [Level 1](../level_1/README.md)
4. ✅ Configure automatic backups
5. ✅ Start programming!

## 🎓 Additional Resources

- [Official Docker Documentation](https://docs.docker.com/)
- [Livebook Documentation](https://hexdocs.pm/livebook/)
- [Podman Documentation](https://docs.podman.io/)

---

**Ready to program with Docker! 🐳🚀**

