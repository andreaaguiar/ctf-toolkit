# CTF Cheatsheets

This directory holds cheatsheets for CTF competitions and penetration testing.

## Available Cheatsheets

- [Reconnaissance](./reconnaissance.md) - Information gathering techniques
- [Scanning & Enumeration](./scanning-enumeration.md) - Network scanning and service enumeration
- [Gaining Access](./gaining-access.md) - Techniques for exploiting vulnerabilities to gain initial access
- [Common Service Exploits](./common-service-exploits.md) - Exploiting common services (FTP, SSH, SMB, RDP, and more)
- [Privilege Escalation](./privilege-escalation.md) - Methods to escalate privileges on compromised systems
- [Password Cracking & Hashes](./password-cracking-hashes.md) - Tools and techniques for cracking passwords
- [Web Application Attacks](./web-application-attacks.md) - Common web vulnerabilities and exploitation
- [Cryptography](./cryptography.md) - Encryption, decryption, and code-breaking techniques
- [Digital Forensics](./digital-forensics.md) - Techniques for analyzing digital evidence
- [Reverse Engineering](./reverse-engineering.md) - Methods for analyzing and understanding compiled code
- [File Transfer Techniques](./file-transfer.md) - Methods to transfer files between systems
- [Maintaining Access](./maintaining-access.md) - Persistence mechanisms
- [Useful Commands & Tips](./useful-commands.md) - General purpose commands and tips

## How to Use

Each cheatsheet contains:

1. Common commands and their usage
2. Explanations of techniques
3. Examples for specific scenarios

### Placeholder Conventions

The cheatsheets use placeholder variables. Replace each one with your own value:

- `<TARGET_IP>` - The IP address of the target system
- `<TARGET_DOMAIN>` - The domain name of the target (e.g., example.com)
- `<PORT>` - The port number for the service you're targeting
- `<USERNAME>` - A username for authentication attempts
- `<PASSWORD>` - A password for authentication attempts
- `<WORDLIST>` - Path to a wordlist file (e.g., /usr/share/wordlists/rockyou.txt)
- `<ATTACKER_IP>` - Your attacking machine's IP address

## Contributing

To contribute to these cheatsheets:

1. Make sure the information is accurate and clear
2. Match the formatting of the existing documents
3. Add examples where possible
