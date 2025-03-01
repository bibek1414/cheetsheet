# Developer Cheat Sheet

A comprehensive cheat sheet for essential and advanced commands across various technologies including Linux, Git & GitHub, Docker, Django, Python, JavaScript, React, and Next.js.

## Table of Contents
1. [Linux](#linux)
   - [File and Directory Management](#file-and-directory-management)
   - [User  and Group Management](#user-and-group-management)
   - [Process Control and System Monitoring](#process-control-and-system-monitoring)
   - [Networking Commands](#networking-commands)
   - [Package Management](#package-management)
   - [Bash Scripting Basics](#bash-scripting-basics)
2. [Git & GitHub](#git--github)
3. [Docker](#docker)
4. [Django](#django)
5. [Python](#python)
6. [JavaScript](#javascript)
7. [React](#react)
8. [Next.js](#nextjs)

---

## Linux

### File and Directory Management
```bash
# List files and directories
ls -la

# Change directory
cd /path/to/directory

# Create a new directory
mkdir new_directory

# Remove a file
rm filename.txt

# Remove a directory
rm -r directory_name
```
### User and Group Management

# Add a new user
sudo adduser username

# Delete a user
sudo deluser username

# Add user to a group
sudo usermod -aG groupname username

# Change file ownership
sudo chown user:group filename
