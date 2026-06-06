# Linux Fundamentals Notes
## Contents

- Introduction to Linux
- Linux Terminal Basics
- Navigating the File System
- Finding Files and Data
- Linux Operators
- SSH
- Command Arguments and Switches
- File Management
- Linux Permissions
- Important Linux Directories
- Text Editors
- File Transfer Techniques
- Process Management
- Service Management
- Cron Jobs
- Package Management
- Linux Logs

## Introduction to Linux

Linux is a free and open-source operating system based on UNIX. It is widely used in servers, cloud environments, embedded devices, industrial systems, and cybersecurity.

### Where Linux is Used

* Web servers
* Cloud infrastructure
* Industrial control systems
* Embedded devices
* IoT systems
* Cybersecurity and penetration testing
* Point of Sale (POS) systems

### Popular Linux Distributions

* Ubuntu
* Debian
* Kali Linux
* Fedora
* Arch Linux

---

# Linux Terminal Basics

The terminal allows users to interact with the operating system using commands.

## Basic Commands

| Command | Description              |
| ------- | ------------------------ |
| echo    | Display text             |
| whoami  | Display current username |
| pwd     | Print working directory  |
| ls      | List files and folders   |
| cd      | Change directory         |
| cat     | Display file contents    |

### Examples

```bash
echo Hello
whoami
pwd
ls
cd Documents
cat notes.txt
```

---

# Navigating the File System

### List Files

```bash
ls
```

### Change Directory

```bash
cd Pictures
```

### Print Current Directory

```bash
pwd
```

### Display File Contents

```bash
cat notes.txt
```

---

# Finding Files and Data

## Using find

Search for files and directories.

```bash
find / -name passwords.txt
find /home -name "*.txt"
```

## Using grep

Search for text within files.

```bash
grep "password" notes.txt
```

Recursive search:

```bash
grep -r "PASSWORD" /etc
```

---

# Linux Operators

## Background Operator (&)

Runs a command in the background.

```bash
command &
```

## Pipe Operator (|)

Passes output from one command to another.

```bash
cat users.txt | grep admin
```

## Redirection (>)

Saves output to a file.

```bash
echo hello > file.txt
```

## Append (>>)

Adds output to an existing file.

```bash
echo hello >> file.txt
```

---

# SSH (Secure Shell)

SSH allows secure remote access to another machine over an encrypted connection.

### Benefits

* Secure remote administration
* Encrypted communication
* Secure file transfers

### Example

```bash
ssh username@192.168.1.10
```

---

# Command Arguments and Switches

Many Linux commands accept options and switches.

### Examples

```bash
ls -l
ls -a
ls -la
```

View command documentation:

```bash
man ls
```

---

# File Management

## Create File

```bash
touch notes.txt
```

## Create Directory

```bash
mkdir projects
```

## Copy Files

```bash
cp file1.txt file2.txt
```

## Move or Rename Files

```bash
mv old.txt new.txt
```

## Delete File

```bash
rm notes.txt
```

## Delete Directory

```bash
rm -r projects
```

## Identify File Type

```bash
file notes.txt
```

---

# Linux Permissions

Linux permissions determine who can access files and directories.

### Permission Values

| Permission  | Value |
| ----------- | ----- |
| Read (r)    | 4     |
| Write (w)   | 2     |
| Execute (x) | 1     |

### Example

```bash
chmod 755 script.sh
```

Meaning:

* Owner: rwx (7)
* Group: r-x (5)
* Others: r-x (5)

---

# Switching Users

Switch to another user account.

```bash
su username
```

Switch to root:

```bash
sudo su
```

---

# Important Linux Directories

## /etc

Stores configuration files.

Examples:

```text
/etc/passwd
/etc/shadow
/etc/sudoers
```

---

## /var

Stores variable data and logs.

```text
/var/log
```

---

## /root

Home directory of the root user.

---

## /tmp

Temporary storage directory.

Files are usually removed after reboot.

---

# Text Editors

## Nano

Beginner-friendly text editor.

```bash
nano notes.txt
```

Common Nano shortcuts:

* Ctrl + O → Save
* Ctrl + X → Exit
* Ctrl + K → Cut line
* Ctrl + U → Paste line

---

## Vim

Advanced text editor.

```bash
vim notes.txt
```

Benefits:

* Powerful editing
* Fast navigation
* Widely used by system administrators

---

# File Transfer Techniques

## SCP

Securely transfer files between systems.

```bash
scp file.txt user@host:/home/user/
```

Example:

```bash
scp notes.txt arnav@192.168.1.10:/home/arnav/
```

---

## Python HTTP Server

Host files temporarily using Python.

```bash
python3 -m http.server 8000
```

Access from browser:

```text
http://IP_ADDRESS:8000
```

---

# Process Management

View running processes:

```bash
ps
```

Interactive process viewer:

```bash
top
```

Kill process:

```bash
kill PID
```

Force kill process:

```bash
kill -9 PID
```

Run process in background:

```bash
command &
```

---

# Service Management

View service status:

```bash
systemctl status apache2
```

Start service:

```bash
systemctl start apache2
```

Stop service:

```bash
systemctl stop apache2
```

Restart service:

```bash
systemctl restart apache2
```

Enable service at boot:

```bash
systemctl enable apache2
```

---

# Cron Jobs

Cron is used to schedule tasks automatically.

Edit cron jobs:

```bash
crontab -e
```

Example:

```bash
0 9 * * * backup.sh
```

Runs every day at 9:00 AM.

Cron Format:

```text
MIN HOUR DOM MON DOW COMMAND
```

---

# Package Management

Update repositories:

```bash
sudo apt update
```

Upgrade packages:

```bash
sudo apt upgrade
```

Install package:

```bash
sudo apt install nmap
```

Remove package:

```bash
sudo apt remove nmap
```

---

# Linux Logs

Most logs are stored in:

```text
/var/log
```

Common log files:

* auth.log
* syslog
* kern.log
* apache2/access.log
* apache2/error.log

Logs help with:

* Troubleshooting
* Monitoring
* Security investigations
* Incident response

---

# Key Skills Learned

* Linux navigation
* Command-line usage
* File management
* Directory management
* File searching
* Text searching
* Linux permissions
* SSH
* SCP
* Process management
* Service management
* Cron jobs
* Package management
* Log analysis

---

# Tools Practiced

* Linux Terminal
* SSH
* Nano
* Vim
* SCP
* grep
* find
* ps
* top
* systemctl
* apt

These fundamentals form the foundation for system administration, penetration testing, incident response, and cybersecurity operations.
