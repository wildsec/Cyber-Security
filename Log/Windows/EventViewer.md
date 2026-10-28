
## Types

|Log Type|Usage|Example|
|---|---|---|
|System Logs|The system logs can be helpful in troubleshooting running issues in the OS. These logs provide information on various operating system activities.|- System Startup and shutdown events  <br>- Driver Loading events  <br>- System Error events  <br>- Hardware events|
|Security Logs|The security logs help detect and investigate incidents. These logs provide information on the security-related activities in the system.|-Authentication events  <br>- Authorization events  <br>- Security Policy changes events  <br>- User Account changes events - Abnormal Activity events|
|Application Logs|The application logs contain specific events related to the application. Any interactive or non-interactive activity happening inside the application will be logged here.|- User Interaction events  <br>- Application Changes events  <br>- Application Update events  <br>- Application Error events|
|Audit Logs|The Audit logs provide detailed information on the system changes and user events. These logs are helpful for compliance requirements and can play a vital role in security monitoring as well.|- Data Access events  <br>- System Change events  <br>- User Activity events  <br>- Policy Enforcement events|
|Network Logs|Network logs provide information on the network’s outgoing and incoming traffic. They play crucial roles in troubleshooting network issues and can also be handy during incident investigations.|- Incoming Network Traffic events  <br>- Outgoing Network Traffic events  <br>- Network Connection Logs - Network Firewall Logs|
|Access Logs|The Access logs provide detailed information about the access to different resources. These resources can be of different types, providing us with information on their access.|- Webserver Access Logs  <br>- Database Access Logs - Application Access Logs  <br>- API Access Logs|

## Windows Event Viewer
- **Description:** This field has a detailed information of the activity.
- **Log Name:** The Log Name indicates the log file name.
- **Logged:** This field indicates the time of the activity.
- **Event ID:** Event IDs are unique identifiers for a specific activity.

Here is a table of some important Event IDs in **Windows Operating System.**

| Event ID | Description                                        |
| -------- | -------------------------------------------------- |
| 4624     | A user account successfully logged in              |
| 4625     | A user account failed to login                     |
| 4634     | A user account successfully logged off             |
| 4720     | A user account was created                         |
| 4724     | An attempt was made to reset an account’s password |
| 4722     | A user account was enabled                         |
| 4725     | A user account was disabled                        |
| 4726     | A user account was deleted                         |

### One-Liner get security relevant logs
``` powershell
Get-WinEvent -FilterHashtable @{LogName='Security';Id=4624,4625,4634,4720,4724,4722,4725,4726} -ErrorAction SilentlyContinue | Sort-Object TimeCreated | ForEach-Object { $xml=[xml]$_.ToXml(); $ed=@{}; foreach($d in $xml.Event.EventData.Data){ $ed[$d.Name]=$d.'#text' }; [PSCustomObject]@{TimeCreated=$_.TimeCreated;EventID=$_.Id;Level=$_.LevelDisplayName;Provider=$_.ProviderName;MachineName=$_.MachineName;Task=$_.TaskDisplayName;Opcode=$_.OpcodeDisplayName;Keywords=$_.KeywordsDisplayNames;RecordId=$_.RecordId;ActivityId=$_.ActivityId;ProcessId=$_.ProcessId;ThreadId=$_.ThreadId;EventData=$ed;Message=$_.Message} } | ConvertTo-Json -Depth 6 | Out-File SecurityEvents.json -Encoding UTF8
```
