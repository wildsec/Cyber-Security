

``` bash
vol3 -f wcry.mem [PluginName]
```

Loop everything:
```powershell
for plugin in windows.malfind.Malfind windows.psscan.PsScan windows.pstree.PsTree windows.pslist.PsList windows.cmdline.CmdLine windows.filescan.FileScan windows.dlllist.DllList; do vol3 -q -f wcry.mem $plugin > wcry.$plugin.txt; done
```


| Plugin                    | Description                                                                                                                                                          |
| ------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| windows.pstree.PsTree     | This plugin lists processes in a tree based on their parent process ID.                                                                                              |
| windows.pslist.PsList     | This plugin is used to list all currently active processes in the machine.                                                                                           |
| windows.cmdline.CmdLine   | This plugin is used to list process command line arguments.                                                                                                          |
| windows.filescan.FileScan | This plugin scans for file objects in a particular Windows memory image. The results have more than 1,400 lines.                                                     |
| windows.dlllist.DllList   | This plugin lists the loaded modules in a particular Windows memory image. Due to a text limitation, this one won't have a View Results icon.                        |
| windows.malfind.Malfind   | This plugin is used to lists process memory ranges that potentially contain injected code. There won't be any View Results icon for this one due to text limitation. |
| windows.psscan.PsScan     | This plugin is used to scan for processes present in a particular Windows memory image.                                                                              |

### Preprocessing With Strings
Next, we will preprocess the memory image with the Linux strings utility. We will extract the **ASCII**, 16-bit **little-endian**, and 16-bit **big-endian** strings.
``` bash
strings wcry.mem > wcry.strings.ascii.txt
strings -e l wcry.mem > wcry.strings.unicode_little_endian.txt
strings -e b wcry.mem > wcry.strings.unicode_big_endian.txt
```