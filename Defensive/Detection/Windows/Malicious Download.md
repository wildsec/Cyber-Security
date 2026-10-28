Sysmon can greatly help you detect every attack stage:
```yaml
# 1. Sysmon Event ID 1: Web browser is launched
Image: C:\Program Files (x86)\Microsoft\Edge\Application\msedge.exe
ParentImage: C:\Windows\Explorer.EXE

# 2. Sysmon Event ID 11: A file (usually archive) appears in Downloads
Image: C:\Program Files (x86)\Microsoft\Edge\Application\msedge.exe
TargetFilename: C:\Users\User\Downloads\invoice.zip*

# 3. Sysmon Event ID 11: Optionally, the user unarchives files to some folder
Image: C:\Windows\Explorer.EXE (or C:\Program Files\7-Zip\7zG.exe)
TargetFilename: C:\Users\User\Downloads\invoice.pdf.exe

# 4. Sysmon Event ID 1: The user double-clicks the unarchived file
Image: C:\Users\User\Downloads\invoice.pdf.exe
ParentImage: C:\Windows\Explorer.EXE
```

![[Pasted image 20260313170959.png]]
## Notes on LNK Attachments#
Unlike with binary attachments, LNK files have a very interesting and important capability - they leave little execution trace. Consider the case on the screenshot below, where a user downloaded LNK file that looks like a Google Chrome shortcut, but in fact runs some PowerShell payload.

After the user launches the shortcut - Windows Explorer reads the "Target" field of the LNK and makes it look like explorer.exe launches PowerShell directly. Still, you can identify if it was indeed LNK phishing or another attack vector by looking for the preceding file creation events - LNK files must have appeared somewhere in Downloads before:
![[Pasted image 20260313171222.png]]