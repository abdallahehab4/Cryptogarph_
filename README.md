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
   
    
