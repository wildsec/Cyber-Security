## Attack Techniques Using DNS
- **Fast Flux Hosting**: Adversaries rotate many IPs quickly with short cache times to avoid simple blocks. We need to record and escalate when we identify a domain that resolves to changing IPs within a short period and across different providers.
- **CDN Abuse**: Legitimate CDNs like Cloudflare or Akamai change IPs too, but done within their ASN ecosystem. If the A record points to a major CDN and other values are normal, take note and carry reputation and ownership checks,
- **Typosquatting**: Domains like paypa1[.]com or micros0ft[.]net trick users visually. If a name looks like a brand clone, treat it as high risk and escalate it.
- **IDN (Internationalised Domain Names)**: Attackers exploit Unicode, creating look-alike domains. Decode Punycode, for example xn--ppaypal-3ya[.]com, and compare to known brands using simple online decoder.
### Analyst Workflow
- **Snapshot Current DNS**: Capture A, NS, MX, TXT, SOA, and TTL values for the domain in question using a single page view and simple.
- **Basic Ownership Check**: Use WHOIS to note registrat, creation date and contact pattern, which supports a light ownership picture of the ticket.
- **Interpret Patterns**: Assess whether the DNS behaviour aligns with benign CDN activity or indicates malicious throwaway domain, noting down the details of the changing IPs.
- **Log Evidence**: Save screenshots or JSON extracts DNS and reputation pages to the case file for audit and escalation.
- **Recommend Action**: Based on findings, advise blocking if high risk, monitor if suspicious but inconclusive, or close if determined benign.
## IP Enrichment
**Enrichment** is adding ownership, ASN (Autonomous System Number), geolocation, and service context to an IP so that our decision is evidence-driven. SOC Level 1 analysts must perform this consistently, since IPs are the most common indicators in alert queues.

## RDAP
[[RDAP]]

## Autonomous Systems and Heuristics
[[Autonomous System]]

### Analyst Workflow
- **Start with RDAP**: Confirm netrange, org, ASN, and abuse contacts.
- **Add ASN Context**: Check bgpview.io or ipinfo.io for ASN details and role.
- **Check Geolocation**: Capture country from at least two sources. Record mismatches.
- **Look for rDNS Patterns**: Reverse DNS can hint at hosting type (e.g., *[.]btcentralplus[.]com = UK broadband). Do not base decisions solely on rDNS.
- **Consult Internal Logs**: Has this IP appeared in the last 30 days? If yes, in what context?
- **Classify Role**: Hosting, residential, CDN, or cloud. Record reasoning.
- **Plan Outreach**: If confirmed malicious and in a cooperative ASN, prepare a report for the abuse contact.

## Reputation and History Matter

- **Check VirusTotal**: Record detection ratio, First Seen, Last Seen, and any community notes.
- **Check Cisco Talos**: Record reputation score and category, noting any changes in the last 30 days.
- **Check IP2Proxy**: Flag if VPN/proxy/Tor; adjust severity accordingly.
- **Check Passive DNS**: Record First Seen, Last Seen, number of IPs in the last 7 days, and ASN spread.
- **Check CT Logs**: Note certificate bursts, suspicious SANs.
- **Cross-Reference with Wayback**: Identify content shifts (benign → phishing).
- **Decision**: Block, monitor, or close, with expiry tied to observed activity.