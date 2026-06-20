# Linux Roadmap (Zero → Professional)

## Phase 0: Environment Setup

### Tools

* Docker (already installed ✅)
* Windows Terminal
* VS Code
* Git

### Lab

Run Ubuntu:

```bash
docker run -it --name ubuntu-lab ubuntu:24.04 bash
```

Practice:

```bash
pwd
ls
whoami
uname -a
cat /etc/os-release
```

Goal:

* Become comfortable with Linux shell.

---

# Phase 1: Linux Basics (Foundation)

## Topics

### Navigation

* pwd
* ls
* cd
* tree
* find

### Files & Directories

* touch
* mkdir
* cp
* mv
* rm

### Viewing Files

* cat
* less
* head
* tail

### Text Processing

* grep
* wc
* cut
* sort
* uniq

### Pipes and Redirection

```bash
>
>>
<
|
```

### Lab

Create:

```
project/
├── logs/
├── config/
└── data/
```

Practice:

* Copy files
* Move files
* Search text
* Redirect output

Example:

```bash
ps aux | grep bash
```

Goal:

* Navigate Linux without thinking.

---

# Phase 2: Users, Groups and Permissions

## Topics

Users

```bash
useradd
passwd
id
who
```

Groups

```bash
groupadd
usermod
```

Permissions

```bash
chmod
chown
chgrp
```

Numeric permissions:

```
755
644
700
777
```

Special permissions

* SUID
* SGID
* Sticky bit

### Lab

Create:

```bash
dev
ops
```

Users:

```bash
alice
bob
```

Experiment with:

```bash
chmod
chown
```

Break permissions and fix them.

Goal:

* Understand permission issues quickly.

---

# Phase 3: Package Management

Ubuntu:

```bash
apt
```

Install:

```bash
curl
vim
git
htop
nginx
```

### Lab

Install nginx:

```bash
apt update
apt install nginx
```

Check:

```bash
nginx -v
```

Goal:

* Manage software like a sysadmin.

---

# Phase 4: Process Management

## Topics

```bash
ps
top
htop
pgrep
kill
killall
jobs
bg
fg
nohup
```

Signals

```
SIGTERM
SIGKILL
SIGINT
```

### Lab

Run:

```bash
sleep 500
```

Find process:

```bash
ps aux | grep sleep
```

Kill it:

```bash
kill PID
```

Goal:

* Debug hanging processes.

---

# Phase 5: Networking

Essential for DevOps.

## Commands

```bash
ip
ss
ping
curl
wget
dig
nslookup
traceroute
netstat
```

### Lab

Inspect:

```bash
ip addr
```

Check ports:

```bash
ss -tulpn
```

Fetch webpage:

```bash
curl google.com
```

DNS:

```bash
dig google.com
```

Goal:

* Troubleshoot network problems.

---

# Phase 6: Storage and Filesystem

## Topics

Filesystem hierarchy

```
/
/etc
/home
/var
/tmp
/proc
```

Commands

```bash
df
du
mount
lsblk
blkid
```

Links

```bash
ln
```

### Lab

Find largest directories:

```bash
du -sh *
```

Create symlink:

```bash
ln -s source target
```

Goal:

* Diagnose disk issues.

---

# Phase 7: Logs and Troubleshooting

Most important for DevOps.

Commands:

```bash
journalctl
dmesg
tail -f
grep
less
```

Locations

```
/var/log
```

### Lab

Watch logs:

```bash
tail -f file.log
```

Search:

```bash
grep ERROR file.log
```

Goal:

* Debug systems confidently.

---

# Phase 8: Services and systemd

Commands:

```bash
systemctl
service
```

Actions

```bash
start
stop
restart
enable
disable
status
```

### Lab

Install nginx

Start:

```bash
systemctl start nginx
```

Check:

```bash
systemctl status nginx
```

Goal:

* Manage services like production servers.

---

# Phase 9: Shell Scripting

Variables

```bash
name=jobayer
```

Conditionals

```bash
if
case
```

Loops

```bash
for
while
```

Functions

Arguments

Exit codes

### Projects

Backup script

```bash
backup.sh
```

Log analyzer

```bash
analyze_logs.sh
```

Disk monitor

```bash
disk_check.sh
```

Goal:

* Automate repetitive tasks.

---

# Phase 10: Advanced Text Processing

Tools

```bash
awk
sed
xargs
cut
tr
paste
sort
uniq
```

### Lab

Analyze logs:

```bash
awk
```

Replace text:

```bash
sed
```

Goal:

* Manipulate data efficiently.

---

# Phase 11: SSH and Remote Administration

Commands

```bash
ssh
scp
rsync
sftp
```

SSH keys

```bash
ssh-keygen
```

### Lab

Generate keys

Connect to another machine

Transfer files

Goal:

* Manage servers remotely.

---

# Phase 12: Performance Monitoring

Commands

```bash
free
vmstat
iostat
uptime
top
htop
sar
```

### Lab

Find:

* High CPU
* High memory
* Disk bottlenecks

Goal:

* Diagnose slow systems.

---

# Phase 13: Linux Internals

Processes

PID

Daemon

Signals

Boot process

Kernel

/proc

Environment variables

### Lab

Explore:

```bash
/proc
```

Inspect:

```bash
cat /proc/cpuinfo
```

Goal:

* Understand how Linux works.

---

# Phase 14: Containers and Linux

Namespaces

Cgroups

OverlayFS

Volumes

### Lab

Using Docker:

```bash
docker exec
docker inspect
docker stats
```

Goal:

* Understand why containers work.

---

# Phase 15: Real DevOps Troubleshooting

Practice scenarios:

### Website down

Check:

```bash
systemctl status nginx
ss -tulpn
journalctl
```

---

### High CPU

Use:

```bash
top
ps
kill
```

---

### Disk full

Use:

```bash
df -h
du -sh
```

---

### Memory issue

Use:

```bash
free -h
vmstat
```

---

### Network issue

Use:

```bash
ping
curl
dig
ss
```

---

# Final Projects

### 1. Linux Log Analyzer

Parse nginx logs with bash.

---

### 2. Server Health Monitor

Monitor:

* CPU
* RAM
* Disk

Send alerts.

---

### 3. Mini Web Server

Install:

* nginx
* SSH

Manage with systemd.

---

### 4. Simulate Production Issues

* Kill nginx
* Fill disk
* Consume memory
* Crash process

Then recover using Linux tools.

---

# Recommended Learning Order

```
1. Basics
2. Permissions
3. Package management
4. Processes
5. Networking
6. Filesystem
7. Logs
8. systemd
9. Shell scripting
10. awk/sed
11. SSH
12. Performance
13. Internals
14. Containers
15. Troubleshooting
```

For DevOps, I'd teach this as a **10-12 week hands-on course**, where each lesson has:

* Theory (20%)
* Hands-on lab (70%)
* Troubleshooting challenge (10%)
