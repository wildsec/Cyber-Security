## Indicator Types Essential to First-Line Triage

Every artefact demands a tailored enrichment path. Memorising tools is less important than recognising what kind of indicator the alert supplies and knowing where to look. Below, we have a table showing the types of indicators we need to be aware of, with examples:

|Indicator|Example|First Resources|Associated IOA or TTP Examples|
|---|---|---|---|
|**IPv4 / IPv6**|`45.155.205.3`|• WHOIS (ASN, allocation date) · VirusTotal Relations· Shodan banner scan|IOA: Repeated SSH failures TTP: `T1110.003` Password Spraying (Password Guessing = `T1110.001`)|
|**Domain / FQDN**|`malicious-updates[.]net`|• WHOIS age · RiskIQ or SecurityTrails passive-DNS · urlscan.io|IOA: surge of DNS queries to a 24-hour-old domain|
|**URL**|`hxxp://malicious-updates[.]net/login`|• URLhaus reputation · urlscan.io behaviour graph · Any.Run dynamic run (network off)|IOA: Browser POST to /gateway.php with payload|
|**File hash**|`e99a18c428cb38d5…`|• VirusTotal static & dynamic · Hybrid-Analysis · MalShare corpus|TTP: T1055 Process Injection into regsvr32.exe|
|**E-mail address**|`billing@evil-corp.com`|• MXToolbox header analysis • Have I Been Pwned|IOA: SPF failure plus recent domain registration|
|**Local artefact**|`HKCU\Software\Run\updater.exe`|• Sigma rules · EDR prevalence query · Vendor knowledge bas|TTP: T1060.001 Registry Run Keys|

> **Actionable tip.** Maintain a browser bookmark folder or a SIEM launcher panel that opens your preferred look-ups with the highlighted indicator pre-populated. The thirty seconds saved per alert compound into hours over a month.