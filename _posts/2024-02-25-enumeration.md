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
```
responder -I <interface> -A
```
Fping Active Checking a Subnet:
```
fping -asgq 172.11.5.0/23
```
Enumerate Users with Kerbrute:
```
kerbrute userenum -d <domain_name> --dc <dc_ip> jsmith.txt -o valid_ad_user_accounts
```

