# Reverse Engineering

## Basic Analysis Tools

```bash
# Check file type
file <binary_file>

# View strings
strings <binary_file>
strings -n 10 <binary_file> | grep -i flag

# List shared library dependencies
ldd <binary_file>

# Examine ELF headers
readelf -h <binary_file>
```

## Dynamic Analysis

```bash
# Basic execution tracing
strace <binary_file>
ltrace <binary_file>

# Run with arguments
strace <binary_file> arg1 arg2

# Attach to running process
strace -p <PID>
```

## GDB Commands

```bash
# Start GDB
gdb <binary_file>

# Basic commands
info functions                     # List functions
disassemble main                   # Disassemble main function
break *0x5655562c                  # Set breakpoint at address
break *main+20                     # Set breakpoint at main+20 bytes
run [args]                         # Run the program with arguments
step / stepi                       # Step through program
continue                           # Continue execution
x/20x $esp                         # Examine memory at ESP
x/s 0x5655562c                     # Examine memory as string
info registers                     # Show register values
```

## Ghidra

```bash
# Basic workflow:
# 1. Create new project
# 2. Import file
# 3. Analyze (accept defaults)
# 4. Double-click function in Symbol Tree
# 5. Look at decompiled C code
```

## Binary Patching

```bash
# Using hexedit
hexedit <binary>

# Using radare2
r2 -w <binary>
[0x00000000]> s 0x5655562c    # Seek to address
[0x5655562c]> wx 9090         # Write NOPs (90 90)
[0x5655562c]> q               # Quit and save
```

## JavaScript and Client-Side Testing

```javascript
// Basic XSS payloads
<script>alert(1)</script>
<img src=x onerror=alert(1)>
<svg/onload=alert(1)>

// JavaScript one-liners to inspect local storage
Object.keys(localStorage).forEach(key => console.log(key, localStorage.getItem(key)));

// Extract JWT token from storage
console.log(localStorage.getItem('jwt_token'));

// Decode JWT token
function parseJwt(token) {
  var base64Url = token.split('.')[1];
  var base64 = base64Url.replace(/-/g, '+').replace(/_/g, '/');
  var jsonPayload = decodeURIComponent(atob(base64).split('').map(function(c) {
    return '%' + ('00' + c.charCodeAt(0).toString(16)).slice(-2);
  }).join(''));
  return JSON.parse(jsonPayload);
};
```

## Browser DevTools Tips

```bash
# Network tab
- Filter requests by type (XHR, JS, CSS)
- Right-click > Copy as cURL
- Inspect WebSocket communication

# Console tab
- Use $$('selector') as shortcut for document.querySelectorAll()
- Use $0 to reference currently selected element in Elements panel
- Use console.table() for viewing structured data

# Sources tab
- Set breakpoints in JavaScript code
- Add watch expressions
- Use conditional breakpoints
```
