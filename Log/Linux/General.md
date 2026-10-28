Linux OS stores all the related logs, such as events, errors, warnings, etc. These are then ingested into SIEM for continuous monitoring. Some of the common locations where Linux stores logs are:

- /var/log/httpd: Contains HTTP Request  / Response and error logs.
- /var/log/cron: Events related to cron jobs are stored in this location.
- /var/log/auth.log and /var/log/secure: Stores authentication-related logs.
- /var/log/kern: This file stores kernel-related events.

Sample cron job:

```shell-session
May 28 13:04:20 ebr crond[2843]: /usr/sbin/crond 4.4 dillon's cron daemon, started with loglevel noticeMay 28 13:04:20 ebr crond[2843]: no timestamp found (user root job sys-hourly)May 28 13:04:20 ebr crond[2843]: no timestamp found (user root job sys-daily) May 28 13:04:20 ebr crond[2843]: no timestamp found (user root job sys-weekly) May 28 13:04:20 ebr crond[2843]: no timestamp found (user root job sys-monthlyJun 13 07:46:22 ebr crond[3592]: unable to exec /usr/sbin/sendmail: cron output for user root job sys-daily to /dev/null
```

## Web Server

It is important to monitor all requests/responses coming in and out of the web server for any potential web attack attempt. In Linux, common locations to write all apache-related logs are /var/log/apache or /var/log/httpd.

Here is an example of Apache Logs:

```shell-session
192.168.21.200 - - [21/March/2022:10:17:10 -0300] "GET /cgi-bin/try/ HTTP/1.0" 200 3395 "-" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/98.0.4758.102 Safari/537.36"127.0.0.1 - - [21/March/2022:10:22:04 -0300] "GET / HTTP/1.0" 200 2216 "-" "curl/7.68.0"
```



## Common Log Files

- `/var/log/auth.log`: Authentication and so on
- `/var/log/kern.log`: Kernel messages and errors, useful for more advanced investigations
- `/var/log/syslog (or /var/log/messages)`: A consolidated stream of various Linux events
- `/var/log/dpkg.log (or /var/log/apt)`: Package manager logs on Debian-based systems
- `/var/log/dnf.log (or /var/log/yum.log)`: Package manager logs on RHEL-based systems
