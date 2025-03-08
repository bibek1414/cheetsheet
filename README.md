# 📌 Comprehensive Developer Cheat Sheet

A comprehensive guide covering Linux, GitHub, Docker, Django, Python, JavaScript, React, Next.js, and more. **Copy-paste ready commands** from **basic to advanced**.

## 📌 Table of Contents
- [Linux Commands](#-linux-commands)
- [Git & GitHub](#-git--github)
- [Docker](#-docker)
- [Docker Volumes](#-docker-volumes)
- [Docker Networking](#-docker-networking)
- [Python](#-python)
- [Django](#-django)
- [JavaScript](#-javascript)
- [React](#-react)
- [Next.js](#-nextjs)

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

### 🔹 File Permissions
```bash
chmod 755 file    # Change file permissions
chown user:group file  # Change file owner
```

### 🔹 System Information
```bash
uname -a          # Print system information
df -h             # Disk space usage
free -h           # Memory usage
lscpu             # CPU information
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
git log --graph --oneline  # Visualize commit history
```

### 🔹 Git Configuration
```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
git config --list  # Show current configuration
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
docker-compose build   # Build or rebuild services
```

---

## 🗃️ Docker Volumes
### 🔹 Volume Management
```bash
# Create a new volume
docker volume create myvolume

# List all volumes
docker volume ls

# Inspect a volume
docker volume inspect myvolume

# Remove a volume
docker volume rm myvolume
```

### 🔹 Volume Mounting
```bash
# Mount a volume
docker run -v myvolume:/app container_name

# Bind mount
docker run -v /host/path:/container/path container_name
```

---

## 🌐 Docker Networking
## 🔍 Basic Network Commands
### List Docker Networks
```bash
# List all networks
docker network ls

# Detailed network information
docker network ls -q  # List network IDs
docker network ls --filter "driver=bridge"  # Filter by driver
```

## 🌉 Network Types in Depth

### 1. Bridge Network (Default Network)
#### Characteristics
- Default network when no network is specified
- Allows containers to communicate internally
- Uses Network Address Translation (NAT) for external communication
- Automatically creates a bridge0 interface

```bash
# Run container on default bridge network
docker run -d --name mycontainer nginx:latest

# Inspect default bridge network
docker network inspect bridge

# List containers on bridge network
docker network inspect bridge | grep -A 10 Containers
```

#### Network Details
- Subnet: Typically 172.17.0.0/16
- Gateway: Usually 172.17.0.1
- DHCP-like IP assignment for containers

### 2. Host Network
#### Characteristics
- Removes network isolation between container and host
- Uses host's network stack directly
- No network namespace separation
- Highest performance, but least secure

```bash
# Run container directly on host network
docker run -d --name host-demo \
  --network=host \
  nginx:latest

# Verify network mode
docker inspect host-demo | grep -i networkmode
```

#### Use Cases
- High-performance networking
- Network monitoring tools
- When you need direct host network access

### 3. Custom Bridge Network
#### Advantages
- Better isolation
- Automatic DNS resolution
- Containers can communicate by container names
- More secure than default bridge

```bash
# Create custom network
docker network create myapp-network

# Run containers on custom network
docker run -d --name webapp \
  --network=myapp-network \
  nginx:latest

docker run -d --name database \
  --network=myapp-network \
  mysql:latest

# Containers can now communicate by name
docker exec webapp ping database
```

## 🔍 Network Inspection

### Detailed Network Inspection
```bash
# Inspect network details
docker network inspect [network-name]

# Inspect specific network properties
docker network inspect bridge -f '{{range .IPAM.Config}}{{.Subnet}}{{end}}'

# Inspect container network details
docker inspect [container-name] | grep -i network
```

## 🛠 Networking Management

### Advanced Network Operations
```bash
# Connect container to additional network
docker network connect [network-name] [container-name]

# Disconnect container from network
docker network disconnect [network-name] [container-name]

# Create network with specific configuration
docker network create \
  --driver bridge \
  --subnet 192.168.0.0/16 \
  --gateway 192.168.0.1 \
  custom-network
```

## 🚀 Advanced Networking

### Network Configuration
```bash
# Create network with specific MTU
docker network create \
  --driver bridge \
  --opt com.docker.network.driver.mtu=1450 \
  limited-network

# Set network aliases
docker run -d --name web \
  --network-alias=myapp \
  --network myapp-network \
  nginx:latest
```

## 🔬 Troubleshooting Network Connectivity

### Connectivity Tools
```bash
# Install network tools in container
docker exec -it container_name /bin/bash
apt-get update
apt-get install -y iputils-ping net-tools

# Test connectivity
ping other-container-name
traceroute other-container-name
netstat -tuln  # List listening ports
```

## 🛡️ Security Considerations

### Network Security Best Practices
```bash
# Disable inter-container communication
docker network create \
  --opt com.docker.network.bridge.enable_icc=false \
  secure-network

# Limit network access
docker run --network=none  # No network access
```

## 💡 Best Practices
1. Use custom bridge networks for better isolation
2. Avoid host network in production
3. Implement network segmentation
4. Use network aliases for service discovery
5. Regularly audit network configurations

## 📊 Performance Optimization
- Minimize network hops
- Use host network for performance-critical apps
- Implement efficient routing
- Monitor network performance

## 🚨 Common Troubleshooting
- Check network configuration
- Verify container network settings
- Test connectivity between containers
- Review Docker network logs

## 🔧 Practical Example Workflow

# Docker Networking Commands Log

## Commands Executed

```sh
cd Docker-Zero-to-Hero
ls
cd examples
git remote -v
ls
docker run -d --name login nginx:latest
docker exec -it login /bin/bash
docker run -d --name logout nginx:latest
docker exec -it login /bin/bash
z devops
cd Docker-Zero-to-Hero
cd examples
docker inspect login
docker inspect logout
docker network ls
docker network ls
docker network create secure-network
docker network ls
docker run -d --name --network secure-network nginx:latest
docker run -d --name finance --network=secure-network nginx:latest
docker s
dockerps
docker ps
docker inspect finance
ls
history
docker exec -it login /bin/bash
docker ps
clear
docker run -d --name host-demo --network=host nginx:latest
docker inspect host-demo
history
docker exec -it login /bin/bash
docker stop $(docker ps -q)
docker rm $(docker ps -a -q)
```

## Summary

- Created and managed Docker containers (`login`, `logout`, `finance`, `host-demo`).
- Created and listed Docker networks (`secure-network`).
- Inspected containers and networks.
- Ran containers with specific networks.
- Stopped and removed all containers.

This log can be used as a reference for Docker networking commands.

## 💥 Common Pitfalls to Avoid
- Using default bridge for production
- Neglecting network security
- Overlooking network performance
- Incorrect port mappings
- Lack of network monitoring

## 📚 Recommended Learning
- Docker official networking documentation
- Network troubleshooting guides
- Container networking best practices
- Performance optimization techniques
---

## 🐍 Python
### 🔹 Virtual Environments
```bash
# Create virtual environment
python3 -m venv myenv

# Activate virtual environment
source myenv/bin/activate  # Linux/Mac
myenv\Scripts\activate     # Windows

# Deactivate
deactivate
```

### 🔹 Package Management
```bash
pip install package_name   # Install a package
pip freeze > requirements.txt  # Export dependencies
pip install -r requirements.txt  # Install from requirements
```

### 🔹 Python Basics
```python
# List comprehension
[x**2 for x in range(10)]

# Lambda function
multiply = lambda x, y: x * y

# Decorators
def my_decorator(func):
    def wrapper():
        print("Before function")
        func()
        print("After function")
    return wrapper
```

---

## 🌐 Django
### 🔹 Project Setup
```bash
# Install Django
pip install django

# Create new project
django-admin startproject myproject
cd myproject

# Create app
python manage.py startapp myapp

# Run migrations
python manage.py makemigrations
python manage.py migrate

# Run development server
python manage.py runserver
```

### 🔹 Django Models
```python
from django.db import models

class MyModel(models.Model):
    name = models.CharField(max_length=100)
    description = models.TextField()
    created_at = models.DateTimeField(auto_now_add=True)
```

---

## 📜 JavaScript
### 🔹 ES6+ Features
```javascript
// Arrow functions
const multiply = (a, b) => a * b;

// Destructuring
const { name, age } = person;

// Spread operator
const newArray = [...oldArray, newItem];

// Promises
fetch(url)
    .then(response => response.json())
    .catch(error => console.error(error));

// Async/Await
async function fetchData() {
    try {
        const response = await fetch(url);
        const data = await response.json();
    } catch (error) {
        console.error(error);
    }
}
```

---

## ⚛️ React
### 🔹 Component Types
```jsx
// Functional Component
function MyComponent() {
    return <div>Hello World</div>;
}

// Class Component
class MyClassComponent extends React.Component {
    render() {
        return <div>Hello World</div>;
    }
}

// Hooks
function HookComponent() {
    const [count, setCount] = useState(0);
    return <div>{count}</div>;
}
```

### 🔹 React Hooks
```jsx
// useState
const [state, setState] = useState(initialValue);

// useEffect
useEffect(() => {
    // Side effect code
    return () => {
        // Cleanup code
    };
}, [dependencies]);

// useContext
const value = useContext(MyContext);
```

---

## 🔀 Next.js
### 🔹 Routing
```jsx
// Page-based routing
pages/index.js       # Route: /
pages/about.js       # Route: /about
pages/users/[id].js  # Dynamic route

// API Routes
pages/api/users.js   # API endpoint: /api/users
```

### 🔹 Server-Side Rendering
```jsx
export async function getServerSideProps(context) {
    const res = await fetch('https://api.example.com/data');
    const data = await res.json();
    
    return {
        props: { data }, // Will be passed to the page component as props
    }
}
```

---

## 💡 Best Practices & Tips
- Always use virtual environments in Python
- Follow PEP 8 guidelines for Python
- Use TypeScript with React for type safety
- Implement proper error handling in async operations
- Use environment variables for sensitive information
- Keep dependencies updated
- Write unit tests for your code
- Use linters and formatters

---

## 🔒 Security Considerations
- Never commit sensitive information to version control
- Use HTTPS for all web communications
- Implement proper authentication and authorization
- Sanitize and validate user inputs
- Keep all software and dependencies updated
- Use security headers in web applications

---

## 📚 Recommended Learning Resources
- MDN Web Docs
- freeCodeCamp
- Coursera
- Udemy
- Official documentation for each technology


# Blanz DevOps Cheatsheet

```sh
vim pod.yml
kubectl create -f pod.yml
kubectl get pods
kubectl get pods -o wide
minikube ssh
kubectl get pods
kubectl delete pod nginx
kubectl get pods
kubectl apply -f pod.yml
kubectl logs nginx
kubectl describe pod nginx
```
