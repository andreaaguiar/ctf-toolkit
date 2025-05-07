# CTF Tools Installation Guide

This document provides installation instructions for the tools referenced in the CTF cheatsheets. Rather than providing a single `requirements.txt` file (which is more appropriate for Python projects with actual code), this guide organizes tools by category and provides system-level installation commands where applicable.

## Table of Contents
- [General Setup](#general-setup)
- [Reconnaissance Tools](#reconnaissance-tools)
- [Scanning & Enumeration Tools](#scanning--enumeration-tools)
- [Web Application Security Tools](#web-application-security-tools)
- [Cryptography Tools](#cryptography-tools)
- [Password Cracking Tools](#password-cracking-tools)
- [Forensics Tools](#forensics-tools)
- [Reverse Engineering Tools](#reverse-engineering-tools)
- [Exploitation Tools](#exploitation-tools)
- [Python-Based Tools](#python-based-tools)

## General Setup

Most CTF tools work best on Linux-based systems. Consider using:
- [Kali Linux](https://www.kali.org/) - Security-focused Linux distribution with many tools pre-installed
- [Parrot OS](https://www.parrotsec.org/) - Another security-focused Linux distribution
- Docker containers for isolated tool environments

## Reconnaissance Tools

```bash
# Install whois, dig, nslookup, host
sudo apt update
sudo apt install -y whois dnsutils bind9-utils

# Install theHarvester
sudo apt install -y theharvester

# Install Recon-ng
sudo apt install -y recon-ng
```

## Scanning & Enumeration Tools

```bash
# Install Nmap
sudo apt install -y nmap

# Install Gobuster
sudo apt install -y gobuster

# Install Nikto
sudo apt install -y nikto

# Install Wfuzz
sudo apt install -y wfuzz

# Install Dirb
sudo apt install -y dirb
```

## Web Application Security Tools

```bash
# Install Burp Suite Community Edition
sudo apt install -y burpsuite

# Install OWASP ZAP
sudo apt install -y zaproxy

# Install SQLmap
sudo apt install -y sqlmap
```

## Cryptography Tools

```bash
# Install basic crypto utilities
sudo apt install -y john openssl xxd

# Install hashcat
sudo apt install -y hashcat

# Install RSATool
git clone https://github.com/ius/rsatool.git
cd rsatool
sudo python setup.py install
```

## Password Cracking Tools

```bash
# Install John the Ripper
sudo apt install -y john

# Install Hashcat
sudo apt install -y hashcat

# Download common wordlists
sudo mkdir -p /usr/share/wordlists
sudo wget -O /usr/share/wordlists/rockyou.txt.gz https://github.com/brannondorsey/naive-hashcat/releases/download/data/rockyou.txt.gz
sudo gunzip /usr/share/wordlists/rockyou.txt.gz
```

## Forensics Tools

```bash
# Install basic forensics utilities
sudo apt install -y foremost binwalk exiftool strings file hexedit

# Install volatility (memory forensics)
sudo apt install -y volatility
```

## Reverse Engineering Tools

```bash
# Install common RE tools
sudo apt install -y gdb ltrace strace radare2

# Install Ghidra (requires manual download)
# Visit https://ghidra-sre.org/ for download and installation instructions
```

## Exploitation Tools

```bash
# Install Metasploit Framework
sudo apt install -y metasploit-framework

# Install searchsploit (ExploitDB)
sudo apt install -y exploitdb
```

## Python-Based Tools

Instead of installing Python packages globally, consider using virtual environments for Python-based tools:

```bash
# Create and activate a virtual environment
python3 -m venv ctf-venv
source ctf-venv/bin/activate

# Install commonly used Python packages for CTFs
pip install requests      # HTTP requests
pip install pwntools      # CTF framework and exploit development library
pip install pycryptodome  # Cryptographic library
pip install scapy         # Packet manipulation
pip install beautifulsoup4 # Web scraping
pip install paramiko      # SSH client
```

### Optional Python packages by category:

#### Web Security
```bash
pip install flask         # For creating mock servers
pip install selenium      # For web automation
```

#### Cryptography
```bash
pip install cryptography  # Higher-level cryptographic library
```

#### Forensics
```bash
pip install python-magic  # File type detection
pip install exifread      # EXIF data extraction
```

#### Utilities
```bash
pip install colorama      # Terminal color formatting
pip install tqdm          # Progress bars
```

## Additional Resources

For a more comprehensive toolkit with actual Python scripts using these dependencies, see the related [pysec-toolkit](https://github.com/andreaaguiar/pysec-toolkit) project.

## Maintaining Your Tools

Keep your tools updated regularly:

```bash
# Update system tools
sudo apt update && sudo apt upgrade -y

# Update Python packages
pip install --upgrade pip
pip list --outdated | cut -d ' ' -f1 | tail -n +3 | xargs -n1 pip install -U
```
