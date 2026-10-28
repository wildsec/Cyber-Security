# Log Ingestion

All these logs provide a wealth of information and can help identify security issues. Each SIEM solution has its own way of ingesting the logs. Some common methods used by these SIEM solutions are explained below:

1. **Agent / Forwarder**  
    These SIEM solutions provide a lightweight tool called an agent (forwarder by Splunk) that gets installed on the Endpoint. It is configured to capture and send all the important logs to the SIEM server.
2. **Syslog**  
    Syslog is a widely used protocol to collect data from various systems like web servers, databases, etc., and send real-time data to the centralized destination.
3. **Manual Upload**  
    Some SIEM solutions, like Splunk, ELK, etc., allow users to ingest offline data for quick analysis. Once the data is ingested, it is normalized and made available for analysis.
4. **Port-Forwarding**  
    SIEM solutions can also be configured to listen on a certain port, and then the endpoints forward the data to the SIEM instance on the listening port.

## Related Topics
- [General](Defensive/SIEM/General.md) - Security Information and Event Management
- [Log Sources](Log%20Sources.md) - Available log sources
- [Splunk](../Defensive/SOC/Tools/Splunk.md) - Splunk SIEM platform
- [Elastic Stack](../Defensive/Tools/Elastic%20Stack.md) - ELK stack
