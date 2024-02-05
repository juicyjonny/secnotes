
## IDENTIFY & ENUMERATE SHARES:

**SMB TOOLS**
Since SMB is a application layer protocol, there are plenty of tools we can use to interact
with it on the network. `smbclient` and the `net.exe` utility (on windows) are good for enumerating SMB shares on any OS.
Get-CIMInstance only works on SMB hosts that are running Windows. `SMBeagle` is a good option
if you need to scan multiple SMB shares. 

**smbclient**
TIP: Some SMB servers will respond with an error protocol negotiation failed if they have disabled SMBv1. To work around this error, add the -m SMB2 argument to smbclient to force the use of the newer SMB protocol.
```
# -L to list shares on the server & deliminate the username and password with %
$ smbclient -L //192.168.1.232 -U jbidden%passwordstringhere

# Connect and interact with SMB share 
$ smbclient //192.168.1.232/PrivateShare -U jbidden%passwordstringhere
```
```
$ net view \\servernameorip /all 
# view remoteshares /all ensures we see administration shares.

$ net share
# view local smb shares
```
```
$ smbeagle -n 192.168.1.0/24 -u username -p password -c smbnetscan.csv
```

**RPC CLIENT:**
This is used to get information over the RPC protocol bundled with SMB server. Not the SMB
fileshares itself. This is incredbilly cool this allows us to communicate with the back-end
RPC service on the host!!!

Common information to get, users, a user sid, server info, group information (domain and local), create new shares,
add users, permissions will still be needed to do this. But can be done over RPC client. 

**SMB PASSWORD ATTACKS:**
SMB is popular to brute force as the protocol itself doesn't delay telling the user 
if authh failed or not. 

**IDENTIFY AND DROP ACTIVE SMB SESSIONS:**

`Get-SmbSession | Select ClientComputerName, Dialect, SecondsExists, SecondsIdle` get active smb sessions on the local computer. 
Close SMB session with `Close-SmbSession`
