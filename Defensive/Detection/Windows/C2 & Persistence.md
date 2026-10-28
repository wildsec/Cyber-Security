* **Attacks Without C2** -> RDP via GUI
* **Simplest C2** -> Phishing Attachment -> click Attachment -> downloads Malware in Temp
## Persistence
![[Pasted image 20260314163135.png]]
## Persisting via RDP
- Create an additional hidden vulnerability in the breached service (e.g. a backdoor or a [web shell](https://attack.mitre.org/techniques/T1505/003/))
- Create a new user ([T1136](https://attack.mitre.org/techniques/T1136/)), make it an administrator ([T1098](https://attack.mitre.org/techniques/T1098/007/)), and use it for further RDP logins

Let's focus on the second method now and see how you or threat actors can manage users on Windows. The first option is to use the graphical utility by searching for "Computer Management" or by launching `lusrmgr.msc`. The second option is to use a command line, like in the example below:

```powershell
# 1. Two methods to create the "mr.backd00r" user
CMD C:\> net user "mr.backd00r" "p@ssw0rd!" /add
PS  C:\> New-LocalUser "mr.backd00r" -Password [...]

# 2. Two methods to add the user to Administrators 
CMD C:\> net localgroup Administrators "mr.backd00r" /add
PS  C:\> Add-LocalGroupMember "Administrators" -Member "mr.backd00r"
```

## Detecting Backdoored Users
[[Event IDs]]

## Malware Persistence

### Services and Tasks

| Persistence Method                                    | Attack Example                                                               | Event ID Logging                                                                                 |
| ----------------------------------------------------- | ---------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------ |
| Create a Windows Service  <br>(Runs after OS startup) | `sc create "BadService" binpath= "C:\malware.exe" start= auto`               | **Launch of sc.exe:** Sysmon / **1**  <br>**Service creation:** Security / **4697  <br>**        |
| Create a Scheduled Task  <br>(Run after OS startup)   | `schtasks /create /tn "BadTask" /tr "C:\malware.exe" /sc onstart /ru System` | **Launch of schtasks.exe:** Sysmon / **1**  <br>**Scheduled task creation:** Security / **4698** |
#### Detecting Services
Many critical Windows components like DNS client or Security Center are services. You can view services by launching **services.msc** or searching for "Services", but you need administrative privileges and the **sc.exe** command to create or modify one.

1. Detect the launch of the `sc.exe create` command via Sysmon event ID **1**
2. Detect service creation via Security event ID **4697** or System event ID [7045](https://www.manageengine.com/products/active-directory-audit/kb/system-events/event-id-7045.html)
3. Detect suspicious processes with a `services.exe` parent process

![[Pasted image 20260314163932.png]]
#### Detecting Tasks
Scheduled tasks are another Windows feature heavily used by both the OS and external apps (e.g. to check for updates or make a backup every hour). From GUI, you can manage tasks by launching **taskschd.msc** or searching for "Task Scheduler". From the command line, you can use the **schtasks.exe** command.

Unlike services, scheduled tasks are very easy to configure and hide, which is why they are the most common persistence method by threat actors, like in these [APT28](https://quointelligence.eu/2020/09/apt28-zebrocy-malware-campaign-nato-theme/#:~:text=Next%2C%20the%20malware%20creates%20a%20new%20scheduled%20task) and [APT41](https://cloud.google.com/blog/topics/threat-intelligence/apt41-us-state-governments/#:~:text=APT41%20has%20leveraged%20the%20following%20Windows%20scheduled%20tasks%20for%20persistence) attacks. Similar to services, you can detect scheduled tasks in three ways:

1. Detect the launch of the `schtasks.exe /create` command via Sysmon event ID **1**
2. Detect and analyze scheduled task creation events via Security event ID **4698**
3. Detect suspicious processes with a `svchost.exe [...] -s Schedule` parent

### Run Keys and Startup

|Persistence Method|Attack Example|Event ID Logging|
|---|---|---|
|Add malware to Startup Folder  <br>(Runs upon user login)|`copy C:\malware.exe   "%AppData%\Microsoft\Windows\Start Menu\Programs\Startup\malware.exe"`|**New startup item:** Sysmon Event ID **11**|
|Add malware to "Run" keys  <br>(Runs upon user login)|`reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\Run"   /v BadKey /t REG_SZ /d "C:\malware.exe"`|**New registry value:** Sysmon Event ID **13**|
#### Detecting Startup
```plaintext
C:\Users\<USER>\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Startup\
Or for all users: C:\ProgramData\Microsoft\Windows\Start Menu\Programs\StartUp
```
The startup folder is not a common choice for legitimate programs, so usually, the folder is empty. Still, threat actors often put their malware there ([Lumma Stealer example](https://www.trendmicro.com/pl_pl/research/25/a/lumma-stealers-github-based-delivery-via-mdr.html#:~:text=We%20also%20observed%20persistence%20being%20established%20through%20the%20Startup%20folder)), and you can detect it by monitoring file creation events (Sysmon Event ID **11**) inside the Startup Folder. Also, note that the programs launched via startup will have an explorer.exe parent, so it may be hard to differentiate them from legitimate user activity
![[Pasted image 20260314165019.png]]

#### Detecting Run Keys
Instead of just copying the program to the startup folder, you need to create a new value in the "Run" Windows registry and put the path to your program there:
```plaintext
HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\RunOr for all users: HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Run
```
![[Pasted image 20260314165100.png]]