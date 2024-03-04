ffuf

## General
| Command                                                                                                                                                     | Description              |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------|
| ffuf -h                                                                                                                                                     | help                     |
| ffuf -w wordlist.txt:FUZZ -u http://SERVER_IP:PORT/FUZZ                                                                                                     | Directory Fuzzing        |
| ffuf -w wordlist.txt:FUZZ -u http://SERVER_IP:PORT/indexFUZZ                                                                                                | Extension Fuzzing        |
| ffuf -w wordlist.txt:FUZZ -u http://SERVER_IP:PORT/blog/FUZZ.php                                                                                            | Page Fuzzing             |
| ffuf -w wordlist.txt:FUZZ -u http://SERVER_IP:PORT/FUZZ -recursion -recursion-depth 1 -e .php -v                                                            | Recursive Fuzzing        |
| ffuf -w wordlist.txt:FUZZ -u https://FUZZ.squid.com/                                                                                                        | Sub-domain Fuzzing       |
| ffuf -w wordlist.txt:FUZZ -u http://squid.com:PORT/ -H 'Host: FUZZ.squid.com' -fs xxx                                                                       | VHost Fuzzing            |
| ffuf -w wordlist.txt:FUZZ -u http://admin.squid.com:PORT/admin/admin.php?FUZZ=key -fs xxx                                                                   | Parameter Fuzzing - GET  |
| ffuf -w wordlist.txt:FUZZ -u http://admin.squid.com:PORT/admin/admin.php -X POST -d 'FUZZ=key' -H 'Content-Type: application/x-www-form-urlencoded' -fs xxx | Parameter Fuzzing - POST |
| ffuf -w ids.txt:FUZZ -u http://admin.squid.com:PORT/admin/admin.php -X POST -d 'id=FUZZ' -H 'Content-Type: application/x-www-form-urlencoded' -fs xxx       | Value Fuzzing            |

-mc : to specify Status code.
-ml: to specify amount of lines in response
-mr: to specify regex pattern
-ms: to specify response size
-mw: to specify amount of words in response

-fw : to filter by the amount of words

-fl : to filter by the number of lines

-fs : to filter by the size of the response

-fc : to filter by the status code

-fr : to filter by the regex pattern


## Wordlists

| Command                                                                    | Description             |
|----------------------------------------------------------------------------|-------------------------|
| /opt/useful/SecLists/Discovery/Web-Content/directory-list-2.3-small.txt    | Directory/Page Wordlist |
| /opt/useful/SecLists/Discovery/Web-Content/web-extensions.txt	Extensions | Wordlist                |
| /opt/useful/SecLists/Discovery/DNS/subdomains-top1million-5000.txt         | Domain Wordlist         |
| /opt/useful/SecLists/Discovery/Web-Content/burp-parameter-names.txt        | Parameters Wordlist     |


```
ffuf -u http://10.10.11.253/FUZZ -w ~/repos/SecLists/Discovery/Web-Content/raft-medium-directories-lowercase.txt
-o ffuf-rootraftmed.log
```
