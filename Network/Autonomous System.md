An **Autonomous System (AS)** is a collection of IP prefixes under a single organisation’s control. Each AS is assigned a unique 16 or 32-bit number (ASN), only required for external communications. Looking at the ASN helps analysts assess the likely role of an IP.

- **Hosting ASNs**: Many small netblocks, often with diverse tenants. Suspicious domains are frequently hosted here.
- **Residential ISPs**: These have huge ranges covering millions of users. Alerts on these may indicate compromised home routers or consumer devices.
- **Cloud/CDN ASNs**: Global anycast, dozens of prefixes, shared edges. Blocking whole ranges here causes collateral damage.

Some heuristic examples of ASN classification include:
- **AS32934 - Facebook/Meta**
- **AS16509 - Amazon AWS**
- **AS124888 - Vodafone**

