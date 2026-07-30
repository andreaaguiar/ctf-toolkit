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

## Memory Forensics (Volatility 3)

```bash
# Volatility 3 auto-detects the OS, so it needs no imageinfo or --profile step.
# The command may be vol, vol3, or python3 vol.py depending on the install.
# For Linux memory dumps, use the linux.* plugins instead of windows.*.

# Process list
vol -f <memory_dump> windows.pslist

# Network connections
vol -f <memory_dump> windows.netscan

# Process command lines
vol -f <memory_dump> windows.cmdline

# Dump a process's memory to output/
vol -f <memory_dump> -o output/ windows.memmap --pid 1234 --dump

# Scan for files in memory
vol -f <memory_dump> windows.filescan

# Dump a file by its physical offset to output/
vol -f <memory_dump> -o output/ windows.dumpfiles --physaddr 0x000000007ea74980
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
