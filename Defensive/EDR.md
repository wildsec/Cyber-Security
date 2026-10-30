# Endpoint Detection and Response

is a security solution that offers deep-level protection for endpoints. No matter where the endpoints are, the EDR will make sure they are monitored constantly and threats are detected

Below are some of the EDR solutions in the market:

- [**CrowdStrike Falcon**](https://www.crowdstrike.com/wp-content/uploads/2022/03/crowdstrike-falcon-insight-data-sheet.pdf)
- [**SentinelOne ActiveEDR**](https://sentinelone.com/resources/datasheets/assets/usecase/sentinel-one-active-#page=1)
- [**Microsoft Defender for Endpoint**](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint)
- [**OpenEDR**](https://www.openedr.com/)
- [**Symantec EDR**](https://docs.broadcom.com/doc/endpoint-detection-and-response-atp-endpoint-en)

## Features
![[Pasted image 20260227083152.png]]
![[Pasted image 20260227092249.png]]
## Telemetry
- **Process Executions and Terminations**  
    It keeps track of all the running and idle processes, which helps to identify suspicious child-parent process relationships, suspicious executables initiating a process, malware payload, etc.
- **Network Connections**  
    All the endpoints' network connections are monitored, which helps identify any connection to a C2 server, unusual port usage, data exfiltration, or lateral movement within the network.
- **Command Line Activity**  
    It captures all the commands executed on the endpoints in CMD, PowerShell, etc., which helps to identify malicious command execution, obfuscated PowerShell script executions, which are often missed by a traditional antivirus.
- **Files and Folders Modifications**  
    Threat actors modify different files and folders during data staging, ransomware executions, and malicious file dropping. The EDR tracks this.
- **Registry Modifications**  
    The registry is a goldmine of information about the configurations in a Windows system. There are many registry modifications that occur during a malicious activity, and most of these are monitored by the EDR.
## Detection
- **Behavioral Detection**  
- **Anomaly Detection**  
- **IOC matching**  
- **MITRE ATT&CK Mapping**  
- **Machine Learning Algorithms**  
## Response
- **Isolate Host**  
- **Terminate Process**  
- **Quarantine**  
- **Remote Access**  
- **Artefacts Collection**

## Related Topics
- [IDS](Intrusion%20Systems/IDS.md) - Intrusion Detection Systems
- [General](SIEM/General.md) - Security Information and Event Management
- [SOC](SOC/General.md) - Security Operations Center
- [ATT&CK](../Frameworks/MITRE/ATT&CK.md) - MITRE ATT&CK Framework for threat mapping
