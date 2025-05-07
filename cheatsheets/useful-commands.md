# Useful Commands & Tips

## User and Password Files

```bash
# View /etc/passwd (encoded)
base64 /etc/passwd | base64 --decode

# View /etc/shadow (encoded)
base64 /etc/shadow | base64 --decode
```

## Server Response Analysis

```text
# Check headers like server or x-powered-by
curl -I http://<TARGET_IP>

# Get all headers
curl -i http://<TARGET_IP>

# Use browser extensions like Wappalyzer
# Intercept requests with Burpsuite
```

## Useful Linux Commands

```bash
# Find setuid binaries
find / -perm -u=s -type f 2>/dev/null

# Find writable directories
find / -writable -type d 2>/dev/null

# Find world-writable files
find / -perm -o+w -type f 2>/dev/null

# View active connections
netstat -tulpn

# View processes
ps aux | grep <process_name>
```

## Useful Windows Commands

```cmd
# View current user and privileges
whoami /all

# View network connections
netstat -ano

# View running services
tasklist /svc

# Search for files
dir /s /b *.txt
```

## Data Extraction

```bash
# Extract credentials from memory dump
strings memdump.bin | grep -i pass

# Search for sensitive information in files
grep -r "password\|username\|key" /path/to/directory

# Extract database contents (SQLite)
sqlite3 database.db .dump
```

## Network Troubleshooting

```bash
# Test connectivity
ping <TARGET_IP>

# Trace route
traceroute <TARGET_IP>

# Check DNS resolution
nslookup <domain>

# View TCP handshake
tcpdump -i eth0 tcp port 80 -n
```
