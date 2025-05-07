# Digital Forensics

## File Analysis

```bash
# File identification
file <file_name>
binwalk <file_name>

# Strings extraction
strings <file_name>
strings -n 10 <file_name> | grep -i password

# Hexdump
hexdump -C <file_name> | head
xxd <file_name> | head

# Extract files from disk images
foremost -i <disk_image> -o output/
```

## Memory Forensics (Volatility)

```bash
# Identify the profile
python vol.py -f <memory_dump> imageinfo

# Process list
python vol.py -f <memory_dump> --profile=Win10x64_18362 pslist

# Network connections
python vol.py -f <memory_dump> --profile=Win10x64_18362 netscan

# Command history
python vol.py -f <memory_dump> --profile=Win10x64_18362 cmdscan

# Dump process memory
python vol.py -f <memory_dump> --profile=Win10x64_18362 memdump -p 1234 -D output/

# Extract files/registry
python vol.py -f <memory_dump> --profile=Win10x64_18362 filescan
python vol.py -f <memory_dump> --profile=Win10x64_18362 dumpfiles -Q 0x000000007ea74980 -D output/
```

## Steganography

```bash
# Check metadata
exiftool <image_file>

# Extract hidden data
steghide extract -sf suspicious_image.jpg -p password
zsteg suspicious_image.png

# Extract data from LSB (Least Significant Bit)
stegsolve.jar # GUI tool for visual analysis

# Check for appended data after EOF
binwalk -e suspicious_image.jpg
foremost suspicious_image.jpg -o output/
```

## PCAP Analysis

```bash
# Basic analysis with Wireshark CLI
tshark -r capture.pcap -Y "http" -T fields -e http.request.method -e http.request.uri
tshark -r capture.pcap -Y "tcp.port == 21" -T fields -e ftp.request.command -e ftp.request.arg

# Extract files from PCAP
foremost -i capture.pcap -o output/

# Extract HTTP objects
wireshark > File > Export Objects > HTTP

# Follow TCP streams
# In Wireshark: Right-click on packet > Follow > TCP Stream
```
