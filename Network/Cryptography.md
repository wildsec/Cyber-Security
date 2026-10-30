Authentication, Authenticity, Integrity, Confidentiality
## Symmetric Encryption
same key to encrypt and decrypt the data

Examples of symmetric encryption are DES (Data Encryption Standard), 3DES (Triple DES) and AES (Advanced Encryption Standard).

## Asymmetric Encryption
pair of keys, one to encrypt and the other to decrypt

Examples are RSA, Diffie-Hellman, and Elliptic Curve cryptography (ECC)
### RSA
- p and q are large prime numbers
- n is the product of p and q
- The public key is n and e
- The private key is n and d
- m is used to represent the original message, i.e., plaintext
- c represents the encrypted text, i.e., ciphertext

### Diffie-Hellman Key Exchange
often used alongside RSA public key cryptography

## Common Operations
### XOR Operation
“exclusive OR”, simple symmetric encryption algorithm
### Modulo Operation
% or as _mod_, none reversible

## SSH-keygen
Generate keys

``` bash
root@TryHackMe# man ssh-keygen 
[...] 
-t dsa | ecdsa | ecdsa-sk | ed25519 | ed25519-sk | rsa Specifies the type of key to create. The possible values are “dsa”, “ecdsa”, “ecdsa-sk”, “ed25519”, “ed25519-sk”, or “rsa”. 
[...]
```

- **DSA (Digital Signature Algorithm)** is a public-key cryptography algorithm specifically designed for digital signatures.
- **ECDSA (Elliptic Curve Digital Signature Algorithm)** is a variant of DSA that uses elliptic curve cryptography to provide smaller key sizes for equivalent security.
- **ECDSA-SK (ECDSA with Security Key)** is an extension of ECDSA. It incorporates hardware-based security keys for enhanced private key protection.
- **Ed25519** is a public-key signature system using EdDSA (Edwards-curve Digital Signature Algorithm) with Curve25519.
- **Ed25519-SK (Ed25519 with Security Key)** is a variant of Ed25519. Similar to ECDSA-SK, it uses a hardware-based security key for improved private key protection.

## GPG
encrypt decrypt and import private key
``` bash 
 gpg --import key
 gpg --decrypt message.gpg
```

## Hash
There is no key, and it’s meant to be impossible (or computationally impractical) to go from the output back to the input.

``` bash
md5sum *.txt
sha1sum *.txt
sha256sum *.txt
```

- **P (Polynomial Time)**: problems solvable in polynomial time.
- **NP (Non-deterministic Polynomial Time)**: problems whose solutions can be verified in polynomial time.

### Windows Passwords
* NTHash / NTLM format
* SAM is store location for account info
* dumping SAM with Mimikatz or AD db: NTDS.dit

### Linux Passwords
On Linux, password hashes are stored in `/etc/shadow`, which is normally only readable by root. They used to be stored in `/etc/passwd`, which was readable by everyone.

|Prefix|Algorithm|
|---|---|
|`$y$`|yescrypt is a scalable hashing scheme and is the default and recommended choice in new systems|
|`$gy$`|gost-yescrypt uses the GOST R 34.11-2012 hash function and the yescrypt hashing method|
|`$7$`|scrypt is a password-based key derivation function|
|`$2b$`, `$2y$`, `$2a$`, `$2x$`|bcrypt is a hash based on the Blowfish block cipher originally developed for OpenBSD but supported on a recent version of FreeBSD, NetBSD, Solaris 10 and newer, and several Linux distributions|
|`$6$`|sha512crypt is a hash based on SHA-2 with 512-bit output originally developed for GNU libc and commonly used on (older) Linux systems|
|`$md5`|SunMD5 is a hash based on the MD5 algorithm originally developed for Solaris|
|`$1$`|md5crypt is a hash based on the MD5 algorithm originally developed for FreeBSD|
### MS Windows Passwords
MS Windows passwords are hashed using NTLM, a variant of MD4. They’re visually identical to MD4 and MD5 hashes, so it’s very important to use context to determine the hash type.

### Crack Password
```
hashcat
john
```


## Definitions
**Hashing**, as already stated, is a process that takes input data and produces a hash value, a fixed-size string of characters, also referred to as digest. 
**Encoding** converts data from one form to another to make it compatible with a specific system. 
Only **encryption**, which we covered in the previous rooms, protects data confidentiality using a cryptographic cipher and a key. 