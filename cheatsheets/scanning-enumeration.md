# Scanning & Enumeration

## Subdomain Enumeration

```bash
# DNSRecon
dnsrecon -t brt -d <TARGET_DOMAIN>

# Sublist3r
./sublist3r.py -d <TARGET_DOMAIN>
```

## Directory Enumeration

```bash
# Gobuster directory enumeration
gobuster dir -u http://<TARGET_IP> -w <WORDLIST>
gobuster dir -u http://<TARGET_IP> -w <WORDLIST>

# With file extensions
gobuster dir -u http://<TARGET_IP> -w <WORDLIST> -x php,txt,html

# Nikto scan
nikto -h http://<TARGET_IP>:<PORT>

# Dirb scan
dirb https://<TARGET_IP>/
```

## Wfuzz

```bash
# Brute force form parameters
wfuzz -c -z file,usernames.txt -z file,passwords.txt --hs "Please enter the correct credentials" -u http://<TARGET_IP>/login.php -d "username=admin&password=FUZZ"
```

## Nmap

```bash
# Quick scan
nmap -sS <TARGET_IP>

# Service Detection
nmap -sV <TARGET_IP>

# OS Detection
nmap -sS -O <TARGET_IP>

# Default scripts
nmap -sS -sC <TARGET_IP>

# Custom script
nmap -sS -n --script "http-date" <TARGET_IP>

# Full port scan
nmap -sS -p1-65335 <TARGET_IP>

# Comprehensive scan
nmap -sS -sV -sC -p <PORTS> <TARGET_IP>
nmap -sV -A -oN nmapscan <TARGET_IP>
```

### Scan Types

```bash
# Stealth SYN Scan
nmap -sS <TARGET_IP>

# Maimon Scan (fin/ack)
nmap -sM <TARGET_IP>

# TCP ACK Scan
nmap -sA <TARGET_IP>

# Window Scan
nmap -sW <TARGET_IP>

# Null Scan (no flags)
nmap -sN <TARGET_IP>

# FIN Scan
nmap -sF <TARGET_IP>

# Xmas Scan (fin, psh, urg)
nmap -sX <TARGET_IP>

# Verbose output
nmap -sS <TARGET_IP> -vv
```

**Nmap scripts location:** `/usr/share/nmap/scripts`
