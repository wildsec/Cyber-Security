
``` bash
#check version
snort -V

#Test config
sudo snort -c /etc/snort/snort.conf -T 
#disable logging
sudo snort -c /etc/snort/snort.conf -N

#Add local rule
sudo nano /etc/snort/rules/local.rules

# Rule testing
sudo snort -q -l /var/log/snort -i lo -A console -c /etc/snort/snort.conf

#Running on PCAP files
sudo snort -q -l /var/log/snort -r Task.pcap -A console -c /etc/snort/snort.conf

#Sniffing 
#with interface
sudo snort -v -i eth0
#just verbose with default interface
sudo snort -v
#dumping packet data mode
sudo snort -d
#dump and link-layer header grabbing
sudo snort -d -e
#full package dum mode 
sudo snort -x

#Logger
#set ownership of generated logs
sudo chown username file
sudo chown username -R directory.
#start logger mode
sudo snort -dev -l.
#ascii format log
sudo snort -dev -K ASCII
#read snort file
sudo snort -r [FILE]
#filter while read by protocol
sudo snort -r logname.log -X
sudo snort -r logname.log icmp
sudo snort -r logname.log tcp
sudo snort -r logname.log 'udp and port 53'
#process only first 10 packages
sudo snort -r logname.log -n 10

#IDS Mode
#start instance without logging
sudo snort -c /etc/snort/snort.conf -N
#background mode
sudo snort -c /etc/snort/snort.conf -D
#alert mode console
sudo snort -c /etc/snort/snort.conf -A console

#IPS Mode (manually) `Q --daq afpacket`
sudo snort -c /etc/snort/snort.conf -q -Q --daq afpacket -i eth0:eth1 -A console

#PCAP Mode
#read multi files with showing
sudo snort -c /etc/snort/snort.conf -q --pcap-list="icmp-test.pcap http2.pcap" -A console --pcap-show

```

| **Parameter**            | **Description**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **-V / --version**       | This parameter provides information about your instance version.                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| **-c**                   | Identifying the configuration file                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| **-T**                   | Snort's self-test parameter allows you to test your setup with this parameter.                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| - **q**                  | Quiet mode prevents Snort from displaying the default banner and initial information about your setup.                                                                                                                                                                                                                                                                                                                                                                                                                                |
| **Sniffing**             | ---                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| **-v**                   | Verbose. Display the TCP/IP output in the console.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| **-d**                   | Display the packet data (payload).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| **-e**                   | Display the link-layer (TCP/IP/UDP/ICMP) headers.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| -**X**                   | Display the full packet details in HEX.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| -**i**                   | This parameter helps define a specific network interface to listen to or sniff. Once you have multiple interfaces, you can choose a specific interface to sniff.                                                                                                                                                                                                                                                                                                                                                                      |
| **Logger**               | ---                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| -l                       | Logger mode, target **log, and alert** output directory. Default output folder is **/var/log/snort**<br><br>The default action is to dump as tcpdump format in **/var/log/snort**                                                                                                                                                                                                                                                                                                                                                     |
| **-K ASCII**             | Log packets in ASCII format.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| -r                       | Reading option: Review the logged events in Snort.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| **-n**                   | Specify the number of packets to be processed or read. Snort will stop after reading the specified number of packets.                                                                                                                                                                                                                                                                                                                                                                                                                 |
| **IDS**/**IPS** **Mode** | ---                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| -c                       | Defining the configuration file.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| -T                       | Testing the configuration file.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| **-N**                   | Disable logging.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| **-D**                   | Background mode.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| **-A**                   | Alert modes;<br><br>**Full:** Full alert mode, providing all possible information about the alert. This mode is also the default; once you use -A and don't specify a mode, Snort defaults to this mode.<br><br>**Fast**: mode displays the alert message, timestamp, source and destination IP addresses**, along with port numbers.<br><br>**Console**: Provides fast style alerts on the console screen.<br><br>**cmg:** CMG style, basic header details with payload in hex and text format.<br><br>**None:** Disabling alerting. |
| **PCAP** **Mode**        | ---                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| **-r / --pcap-single=**  | Read a single pcap                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| **--pcap-list=""**       | Read pcaps provided in command (space separated).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| **--pcap-show**          | Show pcap name on console during processing.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
|                          |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
