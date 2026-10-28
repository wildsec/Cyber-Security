# PowerShell

PowerShell is a task automation and configuration management framework from Microsoft.

## Cmdlets

Cmdlets follow a consistent `Verb-Noun` naming convention. This structure makes it easy to understand what each cmdlet does. The `Verb` describes the action, and the `Noun` specifies the object on which action is performed. For example:

- `Get-Content`: Retrieves (gets) the content of a file and displays it in the console.
- `Set-Location`: Changes (sets) the current working directory.

```powershell
Get-ComputerInfo
Get-LocalUser
Get-NetIPConfiguration
Get-NetIPAddress

Get-Process
Get-Service
Get-NetTCPConnection
Get-FileHash -Path .\ship-flag.txt
Get-Item -Path "C:\House\house_log.txt" -Stream *
```

## Related Topics
- [Bash](Bash.md) - Linux Bash shell
- [Cmd.exe](Cmd.exe.md) - Windows Command Prompt
- [Shell](Shell/General.md) - Shell types and concepts
- [PowerShell Logs](../Log/Windows/PowerShell.md) - PowerShell logging
