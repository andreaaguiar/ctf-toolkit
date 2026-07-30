# CTF Tools Installation Guide

This guide installs the tools used in the CTF cheatsheets. It groups the tools by category and gives system-level install commands. A single `requirements.txt` file does not fit here, because this repository has no Python code of its own. For ready-to-run Python security scripts, see the companion [pysec-toolkit](https://github.com/andreaaguiar/pysec-toolkit) project.

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

Most CTF tools run best on Linux. Use one of these:

- [![Kali Linux](https://img.shields.io/badge/Kali%20Linux-557C94?logo=kalilinux&logoColor=fff)](https://www.kali.org/) - Security-focused Linux distribution with many tools pre-installed
- [![Parrot OS](https://img.shields.io/badge/Parrot%20OS-15E0ED?logo=parrotsecurity&logoColor=fff)](https://www.parrotsec.org/) - Another security-focused Linux distribution
- [![Docker](https://img.shields.io/badge/Docker-2496ED?logo=docker&logoColor=fff)](https://www.docker.com/) - Containers for isolated tool environments

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

# Install RSATool (standalone script)
git clone https://github.com/ius/rsatool.git
cd rsatool
pip3 install gmpy2   # dependency; then run: python3 rsatool.py
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
# (binutils provides strings; libimage-exiftool-perl provides exiftool)
sudo apt install -y foremost binwalk libimage-exiftool-perl binutils file hexedit

# Install Volatility 3 (memory forensics)
sudo apt install -y volatility3
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

Use a virtual environment for Python-based tools instead of installing packages globally:

```bash
# Create and activate a virtual environment
python3 -m venv ctf-venv
source ctf-venv/bin/activate

# Install commonly used Python packages for CTFs
pip3 install requests      # HTTP requests
pip3 install pwntools      # CTF framework and exploit development library
pip3 install pycryptodome  # Cryptographic library
pip3 install scapy         # Packet manipulation
pip3 install beautifulsoup4 # Web scraping
pip3 install paramiko      # SSH client
```

### Optional Python packages by category

#### Web Security

```bash
pip3 install flask         # For creating mock servers
pip3 install selenium      # For web automation
```

#### Cryptography

```bash
pip3 install cryptography  # Higher-level cryptographic library
```

#### Forensics

```bash
pip3 install python-magic  # File type detection
pip3 install exifread      # EXIF data extraction
```

#### Utilities

```bash
pip3 install colorama      # Terminal color formatting
pip3 install tqdm          # Progress bars
```

## Maintaining Your Tools

Update your tools regularly:

```bash
# Update system tools
sudo apt update && sudo apt upgrade -y

# Update Python packages
pip3 install --upgrade pip
pip3 list --outdated | cut -d ' ' -f1 | tail -n +3 | xargs -n1 pip3 install -U
```
