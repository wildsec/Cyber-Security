This utility supports multiple OSs and allows reading and writing through a network.

## Listen
``` bash
nc -lvnp 443
#listening on [any] 4444 ...
```

## Connect
``` bash
nc -nv 10.10.12.230 8080
```
ports below 1024 will require Netcat to be executed with elevated privileges

| Param | Desc                  |
| ----- | --------------------- |
| -l    | listen                |
| -v    | verbose               |
| -n    | prevent DNS for lokup |
| -p    | Port                  |

## Rlwrap
It is a small utility that uses the GNU readline library to provide editing keyboard and history.
``` bash
rlwrap nc -lvnp 443
```
This wraps `nc` with `rlwrap`, allowing the use of features like arrow keys and history for better interaction.

## Ncat
Ncat is an improved version of Netcat distributed by the NMAP project. It provides extra features, like encryption (SSL).

``` bash
ncat -lvnp 4444
ncat --ssl -lvnp 4444
```

## Socat
It is a utility that allows you to create a socket connection between two data sources, in this case, two different hosts.
Listening for reverse shells:
```
socat -d -d TCP-LISTEN:443 STDOUT
```
The command above used the `-d` option to enable verbose output; using it again (`-d -d`) will increase the verbosity of the commands. The `TCP-LISTEN:443` option creates a TCP listener on port `443`, establishing a server socket for incoming connections. Finally, the STDOUT option directs any incoming data to the terminal.