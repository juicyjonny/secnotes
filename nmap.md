## General:
Nmap scan types - can combine scan types such as -sU and -sS (scan UDP and TCP)
| Scan type   | Argument | Description                                                                                                                  |
|-------------|----------|------------------------------------------------------------------------------------------------------------------------------|
| Ping or ARP | -sn      | Disable port scan, host discovry scandepth scans                                                                             |
| TCP connect | -sT      | TCP port scan using conventional TCP connections - 3-Way Handshake Syn,Syn-Ack,Ack                                           |
| TCP SYN     | -sS      | TCP port scan using half-open TCP connections - never sends final Ack. Can look suspicious from network analysis perspective |
| Version     | -sV      | Combine with other scans to identify services through active probes                                                          |


**Host enumeration:**

`sudo nmap -sS -sV -n <IP Address> -oN nmaptop1000.log`

`sudo nmap -sS -sV -p- -oN nmapalltcp.log`  

**Host Discovery:**
`nmap -sn 192.168.0.0/16` -sn disable port scan, just see if host(s) are up.

**NMAP Scripts:**
Stored in `/usr/share/nmap/scripts` by default 
| Nmap Argument         | Description                                                  |
|-----------------------|--------------------------------------------------------------|
| -sC                   | Use nmap default scripts to evaluate the target              |
| --script all          | run all scripts against target (not ideal tbh)               |
| --script=banner       | Run the named script (banner) against the target(s)          |
| --script="http*"      | Run all the scripts beginning with http against the          |
| --script="smb*"       | Run all the scripts beginning with smb against the target(s) |
| --script-help="http*" | Get help and descriptions for the matching named scripts     |
| --script-updatedb     | Update the NSE scripts                                       |



