# Email Defenses

## Technical Defenses

Modern email systems employ various technical controls to help detect and block phishing messages before they reach users.

- [**Email Filtering**](https://www.spamhaus.org/resource-hub/ip-domain-reputation/): Provides filtering based on IP and domain reputation, allowing for blocking or quarantining of suspicious messages.
- [**Secure Email Gateways**](https://www.cloudflare.com/learning/email-security/secure-email-gateway-seg/) (SEGs): Scan messages to detect impersonation attempts, spoofing, and other phishing techniques that other filters might miss.
- [**Link Rewriting**](https://learn.microsoft.com/en-us/defender-office-365/safe-links-about): Replaces suspicious or unknown URLs with safe, redirected ones, giving the system time to scan and verify the link.
- [**Sandboxing**](https://learn.microsoft.com/en-us/defender-office-365/safe-attachments-about): Isolates and tests suspicious links or attachments in a secure, virtual environment to check for malicious behavior.

## DNS-Based Defenses
- [SPF](DNS/Sender%20Policy%20Framework.md) - Sender Policy Framework
- [DKIM](DNS/DomainKeys%20Identified%20Mail.md) - DomainKeys Identified Mail
- [DMARC](DNS/Domain-Based%20Message%20Authentication,%20Reporting,%20and%20Conformance.md) - Domain-based Message Authentication

## User-Facing Tools & Training

Even with strong technical defenses in place, some phishing emails will inevitably reach users. Giving users clear visual cues and education is essential.

- **Trust & Warning Indicators**: Modern email platforms display visual cues to help users understand if a message is safe. A banner may read "External Sender," "Suspicious Link," or signify that a message is from a trusted organization or sender.
- **Phishing Reporting**: Easy, in-email reporting options that let users quickly report suspicious messages.
- **User Awareness Training**: Train employees on identifying phishing attempts, social engineering tactics, and safe email practices.
- **Phishing Simulation Exercises**: Run controlled phishing campaigns to test and reinforce employee training.

## Related Topics
- [Phishing Characteristics](Phishing/Email%20Phishing%20Characteristics.md) - Phishing identification
- [Email Header](Header.md) - Email header analysis
- [Phishing Analysis Tools](Phishing/Analysis%20Tools/) - Tools for analyzing phishing emails
