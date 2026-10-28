
The main components of the Metasploit Framework can be summarized as follows;

- **msfconsole**: The main command-line interface.
- **Modules**: supporting modules such as exploits, scanners, payloads, etc.
- **Tools**: Stand-alone tools that will help vulnerability research, vulnerability assessment, or penetration testing

## vulnerability, exploit, and payload
- **Exploit:** A piece of code that uses a vulnerability present on the target system.
- **Vulnerability:** A design, coding, or logic flaw affecting the target system. The exploitation of a vulnerability can result in disclosing confidential information or allowing the attacker to execute code on the target system.
- **Payload:** An exploit will take advantage of a vulnerability. However, if we want the exploit to have the result we want (gaining access to the target system, read confidential information, etc.), we need to use a payload. Payloads are the code that will run on the target system.

### Auxiliary
Any supporting module, such as scanners, crawlers and fuzzers, can be found here.
``` bash
/opt/metasploit-framework/embedded/framework/modules/auxiliary
```
### Encoders
Encoders will allow you to encode the exploit and payload in the hope that a signature-based antivirus solution may miss them.
``` bash
/opt/metasploit-framework/embedded/framework/modules/encoders
```
### Evasion
While encoders will encode the payload, they should not be considered a direct attempt to evade antivirus software. On the other hand, “evasion” modules will try that, with more or less success.
``` bash
/opt/metasploit-framework/embedded/framework/modules/evasion
```
### Exploits
Exploits, neatly organized by target system.
``` bash
/opt/metasploit-framework/embedded/framework/modules/exploits
```
### NOPs
NOPs (No OPeration) do nothing, literally. They are represented in the Intel x86 CPU family with 0x90, following which the CPU will do nothing for one cycle. They are often used as a buffer to achieve consistent payload sizes.
``` bash
/opt/metasploit-framework/embedded/framework/modules/nops
```
### Payloads
Payloads are codes that will run on the target system.
``` bash
/opt/metasploit-framework/embedded/framework/modules/payloads
```
* **Adapters**: wraps single payloads to convert them into different formats
* **Singles**: Self-contained payloads (add user, launch notepad.exe, etc.) that do not need to download an additional component to run
* **Stagers**: Responsible for setting up a connection channel between Metasploit and the target system
* **Stages**: Downloaded by the stager. This will allow you to use larger sized payloads.

identify single (also called “inline”) payloads and staged payloads.

- generic/shell_reverse_tcp (single payload)
- windows/x64/shell/reverse_tcp (staged payload)
### Post
Post modules will be useful on the final stage of the penetration testing process listed above, post-exploitation.
``` bash
/opt/metasploit-framework/embedded/framework/modules/post
```

## Sessions
Once a vulnerability has been successfully exploited, a session will be created. This is the communication channel established between the target system and Metasploit.
You can use the `background` command to background the session prompt and go back to the msfconsole prompt.