# PuTTY Cheat Sheet

## Basic PuTTY Commands

### 1. Connecting to a Remote Server
To connect to a server, open PuTTY, enter the server's IP address or hostname, and the port (usually 22 for SSH).

- **IP Address/Hostname**: The IP or hostname of the server.
- **Port**: The port number (default for SSH is 22).
- **Connection Type**: Usually SSH.

### 2. Login Commands
After connecting, you'll need to log in to the remote server.

- **Username**: Enter your username when prompted.
- **Password**: Enter your password when prompted (it will not be displayed for security reasons).

---

## Basic Linux Commands in PuTTY

### 1. Navigating Directories
- **Change Directory** (`cd`):
  `cd /path/to/directory`
- **Go to Home Directory**:
  `cd ~`
- **Go to Root Directory**:
  `cd /`
- **Move up one directory**:
  `cd ..`

### 2. List Files and Directories
- **List all files** (`ls`):
  `ls`
- **List detailed file information**:
  `ls -l`
- **List hidden files**:
  `ls -a`

### 3. File Operations
- **Create a file**:
  `touch filename.txt`
- **View file contents**:
  `cat filename.txt`
- **Move or rename a file**:
  `mv oldfilename.txt newfilename.txt`
- **Copy a file**:
  `cp filename.txt /path/to/destination`
- **Delete a file**:
  `rm filename.txt`

### 4. Directory Operations
- **Create a new directory**:
  `mkdir directoryname`
- **Delete a directory**:
  `rmdir directoryname`
- **Delete a directory and its contents**:
  `rm -r directoryname`

---

## SSH Commands and Shortcuts

### 1. Check Current Directory
- **Print Working Directory (PWD)**:
  `pwd`

### 2. Check System Uptime
- **Uptime command**:
  `uptime`

### 3. Check Server Memory Usage
- **Free memory command**:
  `free -h`

### 4. Check Disk Space Usage
- **Disk usage by directories**:
  `du -h`
- **Disk space of entire system**:
  `df -h`

---

## Managing Users and Permissions

### 1. Switch User (SU)
- **Switch to another user**:
  `su username`
- **Switch to root user**:
  `sudo su`

### 2. Change File Permissions
- **Change file owner**:
  `chown owner:group filename`
- **Change file permissions**:
  `chmod 755 filename`

---

## Process Management

### 1. Check Running Processes
- **List processes**:
  `ps aux`

### 2. Kill a Process
- **Kill process by PID**:
  `kill [PID]`

---

## SSH Configuration

### 1. Using SSH Keys
- **Generate an SSH Key Pair**:
  `ssh-keygen -t rsa`
- **Copy SSH key to remote server**:
  `ssh-copy-id username@server_ip`

### 2. SSH Tunneling
- **Create SSH Tunnel**:
  `ssh -L [local_port]:[remote_host]:[remote_port] [username]@[server_ip]`

---

## Common PuTTY Shortcuts

### 1. Close PuTTY Session
- **Exit the terminal**:
  `exit`
- Or simply close the PuTTY window.

### 2. Send `Ctrl + C` Signal
In PuTTY, you can press **Ctrl + C** to terminate a running process or command.

### 3. Send `Ctrl + D` Signal
Press **Ctrl + D** to log out of a session in PuTTY.

---

## File Transfers Using PuTTY (PSCP and PSFTP)

### 1. PSCP (PuTTY Secure Copy Protocol)
PSCP is a command-line tool for securely copying files between computers using SSH.

- **Copy a local file to a remote server**:
  `pscp C:\path\to\file.txt username@server_ip:/path/to/destination`

- **Copy a remote file to your local machine**:
  `pscp username@server_ip:/path/to/file.txt C:\path\to\destination`

### 2. PSFTP (PuTTY Secure File Transfer Protocol)
PSFTP is an interactive file transfer program, similar to FTP, but it uses SSH for secure transfers.

- **Connect to a server using PSFTP**:
  `psftp username@server_ip`

- **Upload a file**:
  `put file.txt`

- **Download a file**:
  `get file.txt`

- **List files on the server**:
  `ls`

