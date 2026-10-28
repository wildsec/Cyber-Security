- **Who, or what, is on the other end of this alert indicator?**
- **What was their behaviour in the past?**
- **How does my organisation respond, and what should I do about it right now?**

![[Pasted image 20260316114526.png]]

## From data to intelligence

|Layer|Definition|Alert-queue example|SOC L1 action|
|---|---|---|---|
|**Data**|An unprocessed observable|`45.155.205.3 :443`|Capture the artefact.|
|**Information**|Data plus factual annotation|_IP registered to Hetzner, first seen 2023-07-14_|Record attributes.|
|**Intelligence**|Analysed information that answers _so-what_|_IP belongs to the current BumbleBee C2; block immediately_|Escalate or suppress.|
During the ascent of data to intelligence, three more labels become paramount for analysts to know.

- **Indicator of Compromise (IOC)**: Evidence of a breach, such as a C2 address in the logs.
- **Indicator of Attack (IOA)**: A malicious action, such as PowerShell launching an unknown service, is underway.
- **Tactics, Techniques, and Procedures (TTP)**: An adversary's detailed methodologies expressed in MITRE ATT&CK IDs ([[ATT&CK]]) and descriptions.

## Feeds & Platforms

**Feed**: A scheduled stream of indicators, usually delivered in various formats such as CSV, JSON, STIX, or through TAXII. Over-ingesting feeds without curation drowns analysts in false positives and erodes trust in the programme.

**Platform**: A structured repository that stores indicators, tracks enrichment, maps relationships, and enforces sharing permissions. **[MISP](https://tryhackme.com/room/misp)** and **[OpenCTI](https://tryhackme.com/room/opencti)** are leading open-source examples.

