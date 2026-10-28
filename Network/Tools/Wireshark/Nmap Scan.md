[[nmap]]
### Scans

TCP Connect scan:
`tcp.flags.syn==1 and tcp.flags.ack==0 and tcp.window_size > 1024`

TCP SYN scan:
`tcp.flags.syn==1 and tcp.flags.ack==0 and tcp.window_size <= 1024`

UDP Scan patterns:
`icmp.type==3 and icmp.code==3`
