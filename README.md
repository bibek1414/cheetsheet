# 📌 Developer Cheat Sheet (Linux, GitHub, Docker, Django, Python, JavaScript, React, Next.js)

A comprehensive cheat sheet covering **Linux, GitHub, Docker, Django, Python, JavaScript, React, Next.js**, and more. **Copy-paste ready commands** from **basic to advanced**.

## 📌 Table of Contents
- [Linux Commands](#linux-commands)
- [Git & GitHub](#git--github)
- [Docker](#docker)
- [Django](#django)
- [Python](#python)
- [JavaScript](#javascript)
- [React](#react)
- [Next.js](#nextjs)

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

---

## 🎯 Django
### 🔹 Basic Django Commands
```bash
django-admin startproject project_name  # Start a Django project
python manage.py startapp app_name  # Create a new app
python manage.py runserver  # Run Django server
python manage.py makemigrations  # Create migrations
python manage.py migrate  # Apply migrations
```

---

## 🐍 Python
### 🔹 Basic Python Commands
```python
print("Hello, World!")  # Print to console
x = input("Enter something: ")  # Get user input
for i in range(5):  # Loop example
    print(i)
def add(a, b):  # Function example
    return a + b
```

---

## ⚡ JavaScript
### 🔹 Basic JavaScript
```js
console.log("Hello, World!");
let name = "John";
const PI = 3.14;
function add(a, b) {
    return a + b;
}
```

### 🔹 Async & Fetch API
```js
async function getData() {
    let response = await fetch('https://api.example.com/data');
    let data = await response.json();
    console.log(data);
}
```

---

## ⚛️ React
### 🔹 Basic React Component
```jsx
import React from 'react';

function Hello() {
    return <h1>Hello, World!</h1>;
}
export default Hello;
```

---

## 🚀 Next.js
### 🔹 API Routes
```js
export default function handler(req, res) {
    res.status(200).json({ message: "Hello from Next.js API!" });
}
```

---

🚀 **This cheat sheet covers all the basic and advanced commands you need!** 🎯
