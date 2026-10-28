see [[Defensive/Tools/Auditd|Auditd]]

``` bash
#
ausearch -i -k proc_wget

# File Events
ausearch -i -k file_sshconf

# anything
ausearch -i | grep "searchme"

# get child processes of ppid
ausearch -i --ppid 3898 

```