# Domain-Based Message Authentication, Reporting, and Conformance (DMARC)

DMARC, an open source standard, uses a concept called alignment to tie the result of two other open source standards, SPF (a published list of servers that are authorized to send email on behalf of a domain) and DKIM (a tamper-evident domain seal associated with a piece of email), to the content of an email.

## DMARC Records

Here is a breakdown of a DMARC record and its components.

`v=DMARC1; p=quarantine; rua=mailto:postmaster@website.com`

- `v=DMARC1`: The version of DMARC (required)
- `p=quarantine` The DMARC policy (quarantine = move to the spam folder)
- `rua=mailto:postmaster@website.com` An optional tag. In this case, aggregate reports will be sent to the email specified

## Related Topics
- [DNS Overview](../../Network/DNS.md) - General DNS concepts
- [SPF](Sender%20Policy%20Framework.md) - Sender Policy Framework
- [DKIM](DomainKeys%20Identified%20Mail.md) - DomainKeys Identified Mail
- [Email Defenses](../Defenses.md) - Email defense mechanisms
