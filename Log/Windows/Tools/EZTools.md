https://ericzimmerman.github.io/#!index.md

## EvtxEcmd
EvtxEcmd is a command-line tool which parses Windows Event Logs into different formats such as CSV, JSON, XML, etc. You may use this tool in conjunction with Timeline Explorer.

``` powershell
.\EvtxECmd.exe -f 'C:\Users\user\Desktop\Incident Files\sysmon.evtx' --csv 'C:\Users\user\Desktop\Incident Files' --csvf sysmon.csv
```
## Timeline Explorer
Timeline Explorer is a GUI-based tool that functions as a data filtering and navigating application to ease incident responders in handling raw data.
Once the logs are loaded, you may navigate through each column﻿ and use the input field to filter specific logs via a unique string.
![[Pasted image 20260319195908.png]]