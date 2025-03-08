# Cryptogarph_
## Crack the hash machine notes :
  1. Identifying Hashing Algorithms : `https://www.tunnelsup.com/hash-analyzer/`
  2. `Hashcat?`
Hashcat is a password recovery tool used for cracking password hashes using various attack methods. It is one of the fastest and most powerful password-cracking tools, supporting multiple hash types and attack modes.
  3. Attack side RSA :
     - ```
       The key variables that you need to know about for RSA in CTFs are p, q, m, n, e, d, and c.
       “p” and “q” are large prime numbers, “n” is the product of p and q.

        The public key is n and e, the private key is n and d.

        “m” is used to represent the message (in plaintext) and “c” represents the ciphertext (encrypted text).```
  4. `ssh-keygen` is the program used to generate pairs of keys most of the time.
  5. John The Ripper :
      - John needs the key in hash format. Use ssh2john.py to extract the hash: `python3 /usr/share/john/ssh2john.py id_rsa > hash.txt`.
      - Crack the Passphrase with John : `john --wordlist=/usr/share/wordlists/rockyou.txt hash.txt`
      - john --show hash.txt.
  6.  decrypt a file using GPG (GNU Privacy Guard) :
       - gpg --import private_key.asc.
       - gpg --decrypt --output decrypted_file.txt file.gpg
         
   ------------------------------------

   
   # Cryptography & Hashcat Commands Cheat Sheet

## **1. Hashcat Commands**
### **Basic Hashcat Syntax:**
```bash
hashcat -a <attack_mode> -m <hash_type> <hash_file> <wordlist>
```
- `-a 0` → Dictionary attack
- `-m <hash_type>` → Specify hash type (e.g., `0` for MD5, `100` for SHA1, `3200` for bcrypt, etc.)
- `<hash_file>` → File containing hashes
- `<wordlist>` → Wordlist file (e.g., `rockyou.txt`)

### **Example: Cracking an NTLM hash using rockyou.txt**
```bash
hashcat -a 0 -m 1000 hash.txt rockyou.txt --force
```

### **Clearing Hashcat Cache & Restarting**
```bash
rm ~/.hashcat/hashcat.potfile
```

## **2. John The Ripper (JTR)**
### **Cracking a hash using John and rockyou.txt:**
```bash
john --wordlist=rockyou.txt --format=<format> hash.txt
```
### **Example: Cracking a SHA1 hash**
```bash
john --wordlist=rockyou.txt --format=raw-sha1 hash.txt
```

### **Show cracked passwords:**
```bash
john --show hash.txt
```

## **3. GPG (GNU Privacy Guard) Encryption & Decryption**
### **Encrypt a file**
```bash
gpg -c file.txt
```
### **Decrypt a file**
```bash
gpg file.txt.gpg
```

## **4. Python XOR Implementation**
```python
def xor_string(s, key):
    return ''.join(chr(ord(char) ^ key) for char in s)

original_text = "label"
key = 13
new_string = xor_string(original_text, key)
print(f"crypto{{{new_string}}}")
```

## **5. Converting Numbers to Binary in Linux & Python**
### **Bash:**
```bash
echo "obase=2; 512" | bc
```
### **Python:**
```python
print(bin(512))  # Output: '0b1000000000'
```

## **6. RSA Cryptography**
### **Installing RsaCtfTool in Linux**
```bash
git clone https://github.com/RsaCtfTool/RsaCtfTool.git
cd RsaCtfTool
pip install -r requirements.txt
```

### **Compute n (RSA modulus) in Python:**
```python
p = 4391
q = 6659
n = p * q
print(n)
```

## **7. ASCII & Unicode Conversions in Python**
```python
print(ord("A"))   # Output: 65
print(ord("€"))   # Output: 8364
print(ord("😃"))  # Output: 128515
```

## **8. Encoding Strings in Hex**
```python
message = "HELLO"
ascii_bytes = [ord(c) for c in message]
hex_bytes = [hex(ord(c)) for c in message]
base_16 = ''.join(hex_bytes).replace("0x", "")
print(f"Base-16: {base_16}")
```

## **9. XOR in Binary (Example)**
```python
x = 512
y = 13
result = x ^ y
print(result)  # Output: 525
```

---
### **📌 Notes:**
- **Use `hashcat -m` to find hash types**
- **Use John The Ripper for alternative cracking methods**
- **Use GPG for file encryption/decryption**
- **XOR is a fundamental operation in cryptography**


    
