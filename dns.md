## DNS
**BRUTE FORCE DISCOVERY:** 
Attempts to enumerate DNS hostnames by brute force guesing of common subdomains

This is deffinetely good for inside a network. But if looking for subdomains on public internet, use `subfinder` (below)


```sh
$ sudo nmap --script=dns-brute --script-args=dns-brute.domain=holidayhackchallenge.com,dns-brute.threads=6,dns-brute.hostlist=./namelist.txt -sS -p 53
```

**Subfinder:** Awesome tool. Automates all this stuff and finds subdomain names.

Example: `subfinder -d domainname.org` for all subdomains it could find.
