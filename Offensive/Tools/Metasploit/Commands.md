
``` bash
#Start command
msfconsole  

msf6 > #Console started

#lists the contents of the folder from which Metasploit was launched
ls

#search
search [anystring]

#use module
use [module|numberfromSearch]
use exploit/windows/smb/ms17_010_eternalblue

#show options
show options

#show auxiliary, payload, exploit, etc.
#The example below lists payloads that can be used with the selected module
show payloads 

#set payload of module
set payload

#get info of selected module/context
info

#info of module

info [module]

#leave context
back

#set options on modulke, RECHECK with [show options]
set [option] [value]

#remove set 
unset
unset all

#set global
setg
unsetg

#launch
exploit (-z for background)
run

#check if system is vuln, some modules have
check

#background session prompt and go back 
background

#see the existing sessions
sessions
sessions -i [number] #interact with session

#list workspaces
workspace

#add workspace
workspace -a

#delete
workspace -d

#options
workspace -h

#select
workspace [workspacename]

#db_nmap, everything saved to database
db_nmap -sV -p- 0.0.0.0

#show hosts (-h)
hosts

#show services(-h)
services

#add db host to RHOSTS
hosts -R

#use multihandler to receive incoming connections
use exploit/multi/handler

```
