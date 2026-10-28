Discovery Commands Coming From "invoice.pdf.exe":
```sql
C:\Users\victim\Downloads\invoice.pdf.exe
├── C:\Windows\System32\cmd.exe
│   ├── ipconfig                                 // Show network settings
│   ├── whoami /priv                             // Show user permissions
│   ├── dir                                      // List current directory
│   ├── net user                                 // List all local users
│   ├── tasklist /v                              // Show running processes
│   └── wmic computersystem get model            // Query for laptop model
└── C:\Windows\...\powershell.exe
    ├── Get-Service	                             // List active services
    └── Get-MpPreference                         // Check MS Defender settings
```
Process Tree for GUI Discovery (e.g. RDP):
```sql
C:\Windows\System32\explorer.exe
├── C:\Windows\System32\cmd.exe                                   // Attacker can still use CMD!
│   └── ...
├── C:\Windows\system32\mmc.exe C:\Windows\system32\compmgmt.msc  // Open Computer Management
├── C:\Windows\system32\control.exe netconnections                // List network adapters
├── C:\Windows\ImmersiveControlPanel\SystemSettings.exe [...]     // Access settings panel
├── C:\Windows\system32\notepad.exe C:\...\secrets.txt            // Read a text file
└── C:\Windows\system32\taskmgr.exe                               // Run Task Manager
```

## Detecting
![[Pasted image 20260314154347.png]]