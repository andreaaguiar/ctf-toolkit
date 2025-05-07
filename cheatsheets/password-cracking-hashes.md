# Password Cracking & Hashes

## Hash Identification

```text
prefix - Algorithm
$1$ - md5crypt, used in Cisco stuff and older Linux/Unix systems
$2$, $2a$, $2b$, $2x$, $2y$ - Bcrypt (Popular for web applications)
$6$ - sha512crypt (Default for most Linux/Unix systems)
```

## Hash Analysis

```text
# Format example
username:$hash_algorithm$hash_salt$hash_data:other_data

# Example
testuser:$6$/5K3q7L0$XsNMzp37s0Q8/sAX0NXtQQjsy6a2f5tvKn2ZJSGWwE8uL9JLhXKpR7.pCbu/WoZa4LXIPYe7k18Z3Nohymk5T0:18233:0:99999:7:::

# Online hash analyzer
https://www.tunnelsup.com/hash-analyzer/
```

## Hashcat

```bash
# Basic usage
hashcat -m <hash-type> -a <attack-type> -o cracked.txt hash.txt <WORDLIST>

# Bcrypt example
hashcat -m 3200 -a 0 -o cracked.txt bycrypt.txt <WORDLIST>

# SHA512crypt example
hashcat -m 1800 <hash_file> <WORDLIST>
```

## John the Ripper

```bash
# Basic usage
john --format=[format] --wordlist=<WORDLIST> <hash_file>

# MD5 example
john --format=raw-md5 --wordlist=<WORDLIST> hash_to_crack.txt

# Linux password files
unshadow passwd.txt shadow.txt > passwords.txt
john --wordlist=<WORDLIST> passwords.txt
```

## Other Password Cracking

```bash
# Zip files
fcrackzip -b --method 2 -D -p <WORDLIST> -v <file_name>.zip

# WPA capture
aircrack-ng -w <WORDLIST> <capture_file>.cap
```
