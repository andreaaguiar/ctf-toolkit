# Cryptography

## Basic Encoding/Decoding

```bash
# Base64 encoding/decoding
echo -n "string" | base64
echo -n "c3RyaW5n" | base64 -d

# Hex encoding/decoding
xxd -p <<< "string"
echo "737472696e67" | xxd -r -p

# ROT13
echo "string" | tr 'A-Za-z' 'N-ZA-Mn-za-m'

# URL encoding/decoding (using Python)
python3 -c "import urllib.parse; print(urllib.parse.quote('string'))"
python3 -c "import urllib.parse; print(urllib.parse.unquote('string%20with%20spaces'))"
```

## Common Ciphers

```bash
# Caesar cipher (using Python)
python3 -c 'import codecs; print(codecs.encode("string", "rot_13"))'

# Vigenère cipher (online tool)
# https://www.dcode.fr/vigenere-cipher

# Substitution cipher (online tool)
# https://www.dcode.fr/substitution-cipher

# RSA basics (using Python pycryptodome)
pip install pycryptodome
# Then use Crypto.PublicKey.RSA and Crypto.Cipher.PKCS1_OAEP modules
```

## Tools for Cryptography

```bash
# RsaCtfTool for automatic RSA cracking
git clone https://github.com/Ganapati/RsaCtfTool.git
cd RsaCtfTool
pip3 install -r requirements.txt
python3 RsaCtfTool.py --publickey ./key.pub --private

# XOR files
python3 -c "open('result', 'wb').write(bytearray(a^b for a,b in zip(open('file1', 'rb').read(), open('file2', 'rb').read())))"

# Frequency analysis
# https://www.dcode.fr/frequency-analysis
```

## Online Resources

- [CyberChef](https://gchq.github.io/CyberChef/) - The Cyber Swiss Army Knife for all encoding/decoding/encryption tasks
- [dcode.fr](https://www.dcode.fr/) - Collection of cipher tools
- [Cryptii](https://cryptii.com/) - Modular conversion, encoding and encryption
- [Online Tools](https://emn178.github.io/online-tools/) - Hash functions and encoding/decoding tools
