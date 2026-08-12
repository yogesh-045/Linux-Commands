# 🔐 Day 17 - File Transfer & Remote Access Commands

File transfer and remote access commands are used to securely connect to remote Linux systems, transfer files, synchronize directories, and communicate with web servers.

These commands are important for Linux administration, SOC operations, incident response, and remote server investigations.

---

# Commands Summary

| Command | Syntax | Description |
|---------|--------|-------------|
| `ssh` | `ssh user@host` | Securely connects to a remote system. |
| `scp` | `scp source user@host:/path` | Securely copies files between systems. |
| `sftp` | `sftp user@host` | Provides an interactive secure file transfer session. |
| `rsync` | `rsync -av source/ destination/` | Synchronizes files and directories efficiently. |
| `wget` | `wget URL` | Downloads files from a URL. |
| `curl` | `curl URL` | Transfers data to or from a server using supported protocols. |

---

# 1. ssh

## Description

`ssh` (Secure Shell) securely connects to a remote Linux or Unix system.

### Syntax

```bash
ssh username@IP
```

### Example

```bash
ssh kali@192.168.1.10
```

### Meaning

```text
ssh      → Secure Shell
kali     → Remote username
IP       → Remote system address
```

### Specify a Port

```bash
ssh -p 2222 kali@192.168.1.10
```

### SOC Analyst Use Case

Connect securely to a remote server during incident investigation or system administration.

---

# 2. scp

## Description

`scp` (Secure Copy Protocol) securely copies files between local and remote systems using SSH.

### Local → Remote

```bash
scp report.txt kali@192.168.1.10:/home/kali/
```

### Remote → Local

```bash
scp kali@192.168.1.10:/home/kali/report.txt .
```

### Copy a Directory

```bash
scp -r logs/ kali@192.168.1.10:/home/kali/
```

### SOC Analyst Use Case

Securely transfer logs, reports, forensic files, or investigation evidence between systems.

---

# 3. sftp

## Description

`sftp` (SSH File Transfer Protocol) provides an interactive and secure way to transfer files between systems.

### Syntax

```bash
sftp username@host
```

### Example

```bash
sftp kali@192.168.1.10
```

### Common Commands

| Command | Description |
|---------|-------------|
| `ls` | Lists remote files. |
| `pwd` | Displays the remote working directory. |
| `cd` | Changes the remote directory. |
| `get` | Downloads a file from the remote system. |
| `put` | Uploads a file to the remote system. |
| `exit` | Exits the SFTP session. |

### Download a File

```bash
get report.txt
```

### Upload a File

```bash
put report.txt
```

### SOC Analyst Use Case

Securely transfer investigation files and logs to or from a remote server.

---

# 4. rsync

## Description

`rsync` synchronizes files and directories between locations efficiently.

It transfers only the data that needs to be updated, making it useful for large datasets and backups.

### Syntax

```bash
rsync -av source/ destination/
```

### Example

```bash
rsync -av logs/ backup/
```

### Remote Example

```bash
rsync -av logs/ kali@192.168.1.10:/home/kali/backup/
```

### Common Options

| Option | Meaning |
|--------|---------|
| `-a` | Archive mode. |
| `-v` | Verbose output. |
| `-r` | Recursively copy directories. |
| `-z` | Compress data during transfer. |

### SOC Analyst Use Case

Synchronize large log collections or investigation data between systems.

---

# 5. wget

## Description

`wget` downloads files and resources from URLs.

### Syntax

```bash
wget URL
```

### Example

```bash
wget https://example.com/file.txt
```

### Download with a Custom Filename

```bash
wget -O report.txt https://example.com/file.txt
```

### SOC Analyst Use Case

Download publicly available security tools, threat intelligence files, or investigation resources.

> **Security Note:** Only download files from trusted sources and verify their integrity when handling security-sensitive files.

---

# 6. curl

## Description

`curl` transfers data to or from a server using protocols such as HTTP, HTTPS, FTP, and others.

### Syntax

```bash
curl URL
```

### Example

```bash
curl https://example.com
```

### Download a File

```bash
curl -O https://example.com/file.txt
```

### Display HTTP Headers

```bash
curl -I https://example.com
```

### SOC Analyst Use Case

Inspect HTTP responses, test web services, troubleshoot connectivity, and investigate suspicious URLs.

---

# Common SOC Analyst Commands

```bash
ssh kali@192.168.1.10

scp report.txt kali@192.168.1.10:/home/kali/

sftp kali@192.168.1.10

rsync -av logs/ backup/

wget https://example.com/file.txt

curl -I https://example.com
```

---

# 🎤 Interview Questions

### 1. What is SSH?

**Answer:**

SSH (Secure Shell) is a protocol used to securely connect to and manage remote systems over an encrypted connection.

---

### 2. What is the difference between SSH and SCP?

**Answer:**

- `ssh` is primarily used for remote login and command execution.
- `scp` is used to securely copy files between systems using SSH.

---

### 3. What is SFTP?

**Answer:**

SFTP (SSH File Transfer Protocol) provides secure interactive file transfer over an SSH connection.

---

### 4. What is the difference between SCP and SFTP?

**Answer:**

- `scp` is mainly used for straightforward file and directory copying.
- `sftp` provides an interactive session with commands such as `get`, `put`, `ls`, and `cd`.

---

### 5. What is rsync used for?

**Answer:**

`rsync` synchronizes files and directories efficiently by transferring only the data that needs to be updated.

---

### 6. What is the difference between wget and curl?

**Answer:**

- `wget` is commonly used for downloading files and recursive web content.
- `curl` is commonly used for transferring data, testing APIs, inspecting HTTP responses, and downloading files.

---

### 7. How can you copy a file from a remote server to your local machine using SCP?

**Answer:**

```bash
scp username@remote_ip:/path/to/file .
```

The `.` represents the current local directory.

---

### 8. How can you securely connect to a remote Linux server?

**Answer:**

Using SSH:

```bash
ssh username@remote_ip
```

---

# 🧪 Practice Lab

> Use only systems that you own or have explicit authorization to access.

### SSH

```bash
ssh username@remote_ip
```

### SCP

```bash
scp report.txt username@remote_ip:/home/username/
```

### SFTP

```bash
sftp username@remote_ip
```

Inside SFTP:

```bash
ls
pwd
get report.txt
put report.txt
exit
```

### Rsync

```bash
rsync -av logs/ backup/
```

### Wget

```bash
wget https://example.com/file.txt
```

### Curl

```bash
curl https://example.com
```

---

# 🎯 Quick Revision

| Command | Remember |
|---------|----------|
| `ssh` | Remote secure login |
| `scp` | Secure file copy |
| `sftp` | Interactive secure file transfer |
| `rsync` | Efficient file synchronization |
| `wget` | Download from URL |
| `curl` | Transfer/request data from servers |

---

# Summary

File transfer and remote access commands are essential for securely managing Linux systems and transferring investigation data.

SOC Analysts commonly use `ssh` for remote access, `scp` and `sftp` for secure file transfers, `rsync` for synchronization, and `curl` or `wget` for interacting with web resources.

Understanding these commands is important for incident response, remote administration, forensic investigations, and security operations.
