Note that while most of the sensitive data is stored as simple files, the secrets can also be hidden in the registry or in process memory. You can review the common Collection targets in the code block below:
```shell
# [Goal: Blackmail Victim] Photos, Chats, Browser History
C:\Users\<user>\AppData\Roaming\Signal\*
C:\Users\<user>\AppData\Local\Google\Chrome\User Data\Default\History

# [Goal: Steal Money] Web Banking Sessions, Crypto Wallets
C:\Users\<user>\AppData\Roaming\Bitcoin\wallet.dat
C:\Users\<user>\AppData\Local\Google\Chrome\User Data\Default\Cookies

# [Goal: Steal Corporate Data] SSH Credentials, Databases
C:\Users\<user>\.ssh\*
C:\Program Files\Microsoft SQL Server\...\DATA\*
```

## Exfiltrating Data
Data collection can be performed automatically via scripts or manually by human threat actors. For scripts, the whole process usually takes less than a minute, but it may take hours for the attacker to find and review the interesting files. Still, both methods should eventually end with exfiltration - uploading stolen data to a controller server. Here, threat actors can be very creative - to avoid detection, they often:

- Exfiltrate stolen data to DropBox, Mega, Amazon S3, or other trusted cloud storage services ([Examples](https://attack.mitre.org/techniques/T1567/002/#:~:text=Procedure%20Examples))
- Exfiltrate stolen data to known code repositories like GitHub or messengers like Telegram ([Example](https://cyberint.com/blog/research/the-new-infostealer-in-town-the-continental-stealer/#:~:text=offers%20a%20Telegram%20bot%20notification%20feature%20that%20informs%20users))
- Or just create a trustworthy-looking domain like "windows-updates.com" and send the data there
## Detecting
|Command Example|Description|
|---|---|
|`notepad.exe C:\Users\<user>\Desktop\finances-2025.csv`|Threat actors used Notepad to check content of the interesting file|
|CMD: `type debug-logs.txt \| findstr password > C:\Temp\passwords.txt`|Threat actors searched for the "password" keyword in a specific file|
|PowerShell: `Get-ChildItem C:\Users\<user> -Recurse -Filter *.pdf`|Threat actors searched for PDF files in the user's home folder|
|PowerShell: `copy C:\Users\<user>\AppData\Roaming\Signal С:\Temp\`|Threat actors copied Signal chat history to the Temp directory|
|PowerShell: `Compress-Archive С:\Temp\ С:\Temp\stolen_data.zip`|Threat actors archived the stolen data, preparing for exfiltration|
|`7za.exe a -tzip C:\Temp\stolen_data.zip С:\\Temp\\*.*`|Alternatively, threat actors can use the existing archiving software like 7-Zip|
