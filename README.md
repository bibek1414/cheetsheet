# 📌 Developer Cheat Sheet (Linux, GitHub, Docker, Django, Python, JavaScript, React, Next.js)

A comprehensive cheat sheet covering **Linux, GitHub, Docker, Django, Python, JavaScript, React, Next.js**, and more. **Copy-paste ready commands** from **basic to advanced**.

## 📌 Table of Contents
- [Linux Commands](#linux-commands)
- [Git & GitHub](#git--github)
- [Docker](#docker)
- [Django](#django)

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




