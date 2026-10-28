
[[Network/DNS|DNS]] (Domain Name System) translates human-friendly domain names (e.g., `example.com`) into IP addresses and provides other record types (A, AAAA, TXT, MX, CNAME, etc.). Key points:

- DNS queries are ubiquitous: almost every host performs DNS lookups.
- DNS is normally allowed through firewalls and gateways, making it an attractive covert channel.
- DNS uses UDP (mostly) on port 53 for queries and responses; TCP is used for zone transfers or large responses.
### Indicators of attack
- Many DNS queries are sent to a single external domain, especially with very high counts compared to the baseline.
- Long subdomain labels or unusually long full query names (> 60–100 characters).
- High entropy or Base32/Base64-like patterns in the query name (lots of mixed case letters, digits, `-`, `=` signs for base64).
- Rare record types (TXT, NULL) or many large TXT responses.
- Unusual response behavior: frequent NXDOMAIN (if attacker uses exfil-by-query without answering), or TCP/large UDP fragments for DNS.
- Queries at regular intervals (beaconing behaviour).

## Wireshark (pcap)
**Filter:** `dns && frame.len > 70`
**Filter:** `dns && dns.qry.name contains <REDACTED>`

## Splunk
`... | stats count by src_ip`
`... | stats count by query | sort -count`
`... | where len(query) > 30`