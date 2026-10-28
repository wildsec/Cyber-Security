# SIEM

Security Information and Event Management

## Log Sources
[Log Sources](Log%20Sources.md)

## Features

* **Centralized Log Collection**
* **Normalization of Logs**
* **Correlation of Logs**
* **Real-time Alerting**
* **Dashboards and Reporting**

## Related Topics
- [SOC](SOC/General.md) - Security Operations Center
- [Log Sources](Log%20Sources.md) - Available log sources
- [Splunk](SOC/Tools/Splunk.md) - Splunk SIEM platform
- [IDS](Intrusion%20Systems/IDS.md) - Intrusion Detection Systems
- [EDR](EDR.md) - Endpoint Detection and Response

## Time Pitfalls
One common challenge analysts face when working in a SIEM is time, specifically how time is recorded across different log sources.  
Logs can come from systems in different time zones. Some сan be in UTC, others in local time, and some may not include a timezone at all.

## Logs Normalisation
Different logs come in various formats. Some are in JSON, others in XML, or even plain text. Each system logs events in its own way, using different field names and structures.