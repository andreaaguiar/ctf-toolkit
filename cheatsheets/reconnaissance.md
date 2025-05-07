# Reconnaissance

## OSINT

```bash
# Google dorks for subdomain discovery
-site:www.<TARGET_DOMAIN> site:*.<TARGET_DOMAIN>

# Find specific file types
site:<TARGET_DOMAIN> filetype:pdf

# Find exposed directories
site:<TARGET_DOMAIN> intitle:"index of"

# Find login pages
site:<TARGET_DOMAIN> inurl:login | admin | portal | signin

# OSINT frameworks
# TheHarvester - gather emails, subdomains, hosts, employee names, etc.
theharvester -d <TARGET_DOMAIN> -l 500 -b google,linkedin

# Social media reconnaissance
# LinkedIn, Twitter, Facebook, Instagram for employee information
```

## SSL/TLS Certificates

```bash
# Search for certificates in crt.sh
https://crt.sh/?q=%.<TARGET_DOMAIN>

# Using curl with crt.sh API
curl -s "https://crt.sh/?q=%.<TARGET_DOMAIN>&output=json" | jq -r '.[] | .name_value' | sort -u

# Certificate transparency logs with certspotter
curl -s "https://api.certspotter.com/v1/issuances?domain=<TARGET_DOMAIN>&include_subdomains=true&expand=dns_names" | jq '.[].dns_names[]' | sort -u
```

## Whois and DNS Enumeration

```bash
# Basic whois lookup
whois <TARGET_DOMAIN>

# DNS lookup
dig <TARGET_DOMAIN> ANY +noall +answer
dig -x <TARGET_IP>

# DNS zone transfer attempt
dig axfr @ns1.<TARGET_DOMAIN> <TARGET_DOMAIN>
```

## Custom Wordlist Generation

```bash
# Basic website wordlist generation
cewl <TARGET_IP> -w output.txt

# Specify spidering depth
cewl <TARGET_IP> -d 2 -w output1.txt

# Set min and max word length
cewl <TARGET_IP> -m 5 -x 10 -w output2.txt
```
