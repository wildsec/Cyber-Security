# DomainKeys Identified Mail (DKIM)

DKIM stands for DomainKeys Identified Mail and is used for the authentication of an email that's being sent. Like SPF, DKIM is an open standard for email authentication that is used for DMARC alignment. A DKIM record exists in the DNS, but it is more complex than SPF. DKIM's advantage is that it can survive forwarding, which makes it superior to SPF and a foundation for securing your email.

![[Pasted image 20260306172522.png]]

## DKIM Records

Here is a sample DKIM record, along with its components.

`v=DKIM1; k=rsa; p=<public_key>`

- `v=DKIM1` Specifies the version of DKIM being used (optional)
- `k=rsa` The key type. The RSA encryption algorithm is standard
- `p=` This is the public key that will be matched to the private key to verify the DKIM signature

Note: DKIM record formats vary and may include other tags depending on the mail provider or implementation.

## Related Topics
- [DNS Overview](../../Network/DNS.md) - General DNS concepts
- [SPF](Sender%20Policy%20Framework.md) - Sender Policy Framework
- [DMARC](Domain-Based%20Message%20Authentication,%20Reporting,%20and%20Conformance.md) - Domain-based Message Authentication
- [Email Defenses](../Defenses.md) - Email defense mechanisms
