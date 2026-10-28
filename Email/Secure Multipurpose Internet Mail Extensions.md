**Secure/Multipurpose Internet Mail Extensions** ([**S/MIME**](https://learn.microsoft.com/en-us/exchange/security-and-compliance/smime-exo/smime-exo)) is a standard protocol for sending digitally signed and encrypted messages. It is based on public key cryptography, where the private key is never shared and the public key can be distributed openly. The two main components and security features of S/MIME are:

**Digital Signature**

The sender signs the message with their private key, the recipient verifies the sender's identity using the sender's public key. This security feature provides:

- **Authentication**: Confirms the sender's identity through their digital certificate
- **Non-repudiation**: Ensures the sender cannot deny sending the message
- **Data Integrity**: Detects any changes to the message after it's signed

**Encryption**

The sender encrypts the message using the recipient's public key, allowing only the recipient to decrypt it with their private key. This security feature provides:

- **Confidentiality**: Keeps the content private and readable only by the intended recipient

![[Pasted image 20260306173630.png]]
