# Sender Policy Framework (SPF)

"Sender Policy Framework (SPF) is used to authenticate the sender of an email. With an SPF record in place, Internet Service Providers can verify that a mail server is authorized to send email for a specific domain. An SPF record is a DNS TXT record containing a list of the IP addresses that are allowed to send email on behalf of your domain."

![[Pasted image 20260306172001.png]]

| Verification Result | Intended Action |
|---------------------|-----------------|
| Pass, Neutral, None | Accept (Allow and process the email) |
| SoftFail | Flag (Mark as suspicious but allow) |
| Fail, PermError | Reject (Permanent rejection, e.g. SMTP 550; PermError = the domain's SPF record is invalid or cannot be interpreted) |
| TempError | Defer (Temporary rejection, e.g. SMTP 451, so the sender retries; TempError = transient DNS error) |

Per RFC 7208 section 8.

## SPF Records

Syntax: https://dmarcian.com/spf-syntax-table/

## Related Topics
- [DNS Overview](../../Network/DNS.md) - General DNS concepts and record types
- [DKIM](DomainKeys%20Identified%20Mail.md) - DomainKeys Identified Mail
- [DMARC](Domain-Based%20Message%20Authentication,%20Reporting,%20and%20Conformance.md) - Domain-based Message Authentication
- [Email Defenses](../Defenses.md) - Email defense mechanisms
