# Infected USB Detection

Detecting infections from USB devices requires monitoring removable media events.

![[Pasted image 20260313171935.png]]

## Detection Indicators

### USB Device Connection
- New USB device plugged in (Event ID 6416 on Windows)
- Unauthorized USB device types
- USB devices outside business hours

### File Activity
- Auto-execution of files from USB
- Suspicious file copies to/from USB
- Known malicious files detected on removable media

### Process Execution
- Processes spawned from USB drive paths
- PowerShell/cmd execution from removable media

## Related Topics
- [Windows Event IDs](../../Log/Windows/Event%20IDs.md)
- [Malicious Download](Malicious%20Download.md)
- [C2 & Persistence](C2%20&%20Persistence.md)
