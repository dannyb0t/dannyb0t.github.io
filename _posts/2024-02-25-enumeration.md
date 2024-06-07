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

