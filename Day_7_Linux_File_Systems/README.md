

## Part 1: Linux File System Hierarchy

### `/` (root)
- Main folder of Linux. Everything starts here.
- Contains: `bin`, `etc`, `home`
- I use this to understand the whole system.

---

### `/home`
- Stores files of normal users.
- Example: `shubham`
- I use this for user files and scripts.

Command:
ls -la ~

---

### `/root`
- Home folder of root (admin) user.
- Contains admin files.
- I use this when working as root.

---

### `/etc`
- Stores configuration files.
- Example: `hostname`, `ssh`
- I use this to change system or service settings.

Command:
cat /etc/hostname

---

### `/var/log`
- Stores logs (system activity records).
- Example: `syslog`, `auth.log`
- I use this to find errors and issues.

Command:
du -sh /var/log/* 2>/dev/null | sort -h | tail -5

---

### `/tmp`
- Temporary files.
- Files may be deleted after reboot.
- I use this for short-time testing.

---

### `/bin`
- Basic system commands.
- Example: `ls`, `cp`
- I use this when system is broken or minimal.

---

### `/usr/bin`
- Normal user commands.
- Example: `python3`, `git`
- I use this to run programs.

---

### `/opt`
- Extra or third-party software.
- Example: custom apps
- I use this for manual installations.

---

## Part 2: Scenario Practice

### Scenario 1: Service Not Starting

Problem: `myapp` service not working after reboot.

Step 1:
systemctl status myapp  
Why: Check service is running or not.

Step 2:
journalctl -u myapp -n 50  
Why: Check error logs.

Step 3:
systemctl is-enabled myapp  
Why: Check if service starts on reboot.

Step 4:
systemctl restart myapp  
Why: Try to start service again.

Lesson:
Check status → check logs → fix issue.

---

### Scenario 2: High CPU Usage

Problem: Server is slow.

Step 1:
top  
Why: See CPU usage live.

Step 2:
ps aux --sort=-%cpu | head -10  
Why: Find which process uses most CPU.

Step 3:
top -p <PID>  
Why: Watch that process.

Lesson:
Find problem process first.

---

### Scenario 3: Service Logs

Problem: Where are Docker logs?

Step 1:
systemctl status docker  
Why: Check service name and status.

Step 2:
journalctl -u docker -n 50  
Why: See recent logs.

Step 3:
journalctl -u docker -f  
Why: Watch logs live.

Lesson:
systemd services use journal logs.

---

### Scenario 4: Permission Problem

Problem: Script not running.

Step 1:
ls -l /home/user/backup.sh  
Why: Check file permission.

Step 2:
chmod +x /home/user/backup.sh  
Why: Add execute permission.

Step 3:
ls -l /home/user/backup.sh  
Why: Confirm permission.

Step 4:
./backup.sh  
Why: Run script.

Lesson:
File needs execute (`x`) permission.

---

## Final Learning

- Always check first, do not guess
- Logs help find problems
- Linux issues are solved step by step
