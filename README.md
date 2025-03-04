# 📌 Developer Cheat Sheet (Linux, GitHub, Docker, Django, Python, JavaScript, React, Next.js)

A comprehensive cheat sheet covering **Linux, GitHub, Docker**, and more. **Copy-paste ready commands** from **basic to advanced**.

## 📌 Table of Contents
- [Linux Commands](#linux-commands)
- [Git & GitHub](#git--github)
- [Docker](#docker)

---

## 🐧 Linux Commands
### 🔹 Basic Commands
```bash
ls -la        # List files with details
pwd          # Print current directory
cd /path     # Change directory
touch file   # Create an empty file
rm file      # Remove a file
mkdir dir    # Create a directory
rmdir dir    # Remove an empty directory
cp file1 file2  # Copy a file
mv file1 file2  # Move/Rename a file
echo "Hello" > file.txt  # Write text to a file
cat file.txt  # Read file contents
```

### 🔹 User & Process Management
```bash
whoami       # Display current user
id user      # Show user ID and groups
ps aux       # Show running processes
kill -9 PID  # Kill a process by PID
top          # Monitor system processes
htop         # Interactive process viewer
```

### 🔹 Networking
```bash
ifconfig         # Show network interfaces (deprecated)
ip a             # Show IP addresses
ping google.com  # Check network connectivity
netstat -tulnp   # Show listening ports
```

---

## 🔗 Git & GitHub
### 🔹 Basic Git Commands
```bash
git init        # Initialize a repository
git clone URL  # Clone a repository
git status     # Show changes
git add file   # Stage a file
git commit -m "Message"  # Commit changes
git push origin branch  # Push changes
git pull origin branch  # Pull updates
git branch     # Show branches
git checkout branch  # Switch branch
```

### 🔹 Advanced Git
```bash
git reset --hard HEAD  # Reset changes
git stash         # Stash changes
git rebase branch  # Rebase branch
git cherry-pick commit_id  # Pick specific commit
```

---

## 🐳 Docker
### 🔹 Basic Docker Commands
```bash
docker pull image_name   # Pull an image
docker run -d -p 8080:80 image_name  # Run a container
docker ps    # List running containers
docker stop container_id  # Stop a container
docker rm container_id  # Remove a container
docker images   # List images
docker rmi image_id  # Remove an image
```

### 🔹 Docker Compose
```bash
docker-compose up -d   # Start containers
docker-compose down    # Stop containers
docker-compose logs    # View logs
```

```
1  sudo apt update
    2  docker --version
    3  sudo apt install docker.io -y
    4  docker --version
    5  sudo systemctl status docker
    6  docker run hello-world
    7  sudo usermod -aG docker ubuntu
    8  docker run hello-world
    9  logout
   10  docker -version
   11  docker run hello-world
   12  git clone https://github.com/iam-veeramalla/Docker-Zero-to-Hero.git
   13  ls
   14  cd Docker-Zero-to-Hero/
   15  ls
   16  cd exm
   17  cd examples/
   18  ls
   19  cd first-docker-file/
   20  ls
   21  vim Dockerfile
   22  docker build -t hello .
   23  docker run -it hello
   24  history
```
# DOcker pull
```
  906  docker pull bibek1414/expensetracker
  907  docker run -d -p 8000:8000 bibek1414/expensetracker:latest\n
```


# Docker Commands Cheat Sheet

## **Docker Volume Commands**
```sh
# Create a new volume
docker volume create bibek

# List all volumes
docker volume ls

# Inspect a volume
docker volume inspect bibek

# Remove a volume
docker volume rm bibek
```

## **Steps to Remove a Docker Volume in Use**
```sh
# Check running/stopped containers
docker ps -a

# Stop the container using the volume
docker stop <container_id>

# Remove the container
docker rm <container_id>

# Remove the volume
docker volume rm <volume_name>
```

## **Docker Image Commands**
```sh
# List images (only first 5 lines)
docker images | head -5

# Build an image using Dockerfile in the current directory
docker build .
```

## **Docker Container Commands**
```sh
# Run a container with a named volume
# (Make sure there is no space after the comma in --mount)
docker run -d --mount source=bibek,target=/app a04dc4851cbc

# Run a container with Nginx using a named volume
docker run -d --mount source=bibek,target=/app nginx:latest

# List running containers
docker ps

# List all containers (including stopped ones)
docker ps -a

# View logs of a specific container
docker logs <container_id>
```

## **Common Errors & Fixes**
- **Incorrect syntax for `--mount`**:
  ```sh
  # Wrong:
  docker run -d --mount source=bibek , targer=/app a04dc4851cbc
  
  # Correct:
  docker run -d --mount source=bibek,target=/app a04dc4851cbc
  ```


  # Docker Networking Cheatsheet

## Basic Network Commands

### List Docker Networks
```bash
docker network ls
```

### Create a Custom Network
```bash
docker network create [network-name]
```
Example:
```bash
docker network create secure-network
```

## Network Types

### 1. Bridge Network (Default)
- Default network when no network is specified
- Containers can communicate with each other
- NAT used for external communication
```bash
# Run container on default bridge network
docker run -d --name mycontainer nginx:latest
```

### 2. Host Network
- Removes network isolation between container and host
- Uses host's network directly
```bash
docker run -d --name host-demo --network=host nginx:latest
```

### 3. Custom Bridge Network
- Better isolation and automatic DNS resolution
- Containers can communicate by container names
```bash
# Create custom network
docker network create myapp-network

# Run containers on custom network
docker run -d --name webapp --network=myapp-network nginx:latest
docker run -d --name database --network=myapp-network mysql:latest
```

## Network Inspection

### Inspect Network Details
```bash
docker network inspect [network-name]
```
Example:
```bash
docker network inspect bridge
```

### Inspect Container Network
```bash
docker inspect [container-name]
```

## Networking Management

### Connect Container to Network
```bash
docker network connect [network-name] [container-name]
```

### Disconnect Container from Network
```bash
docker network disconnect [network-name] [container-name]
```

## Advanced Networking

### Create Network with Specific Subnet
```bash
docker network create --subnet=192.168.0.0/16 custom-subnet-network
```

### Limit Network Bandwidth
```bash
docker run --network-alias=web --net-alias=api \
  --network-driver=bridge \
  --network-opt com.docker.network.driver.mtu=1450 \
  myimage
```

## Troubleshooting Network Connectivity

### Install Ping in Container
```bash
# Inside container
apt-get update
apt-get install iputils-ping -y
```

### Test Connectivity
```bash
# From within a container
ping [container-ip-or-name]
```

## Best Practices
1. Use custom bridge networks for better isolation
2. Avoid using host network except for specific performance needs
3. Use network aliases for service discovery
4. Be mindful of security when configuring networks

## Common Network-Related Docker Commands
```bash
# List running containers
docker ps

# List all networks
docker network ls

# Create a network
docker network create [name]

# Inspect network
docker network inspect [name]

# Connect container to network
docker network connect [network] [container]

# Disconnect container from network
docker network disconnect [network] [container]
```

## Security Considerations
- Use `--icc=false` to disable inter-container communication
- Implement network segmentation
- Use user-defined bridge networks
- Avoid using the default bridge network for production

## Example Workflow
```bash
# Create a custom network
docker network create myapp-network

# Run containers on the network
docker run -d --name web --network myapp-network nginx
docker run -d --name db --network myapp-network mysql

# Containers can now communicate by name
```
- **Mistyped commands (e.g., `dockerps` instead of `docker ps`)** → Ensure correct spelling.

---
### **Tips**
✅ Use `-v` instead of `--mount` for simpler volume mounts:  
```sh
docker run -d -v bibek:/app a04dc4851cbc
```
✅ If the container exits immediately, use:
```sh
docker run -it --mount source=bibek,target=/app a04dc4851cbc /bin/sh
```

