---
layout: post
title: Downloading SplunkBase Apps with Three Commands
comments: false
---

## Downloading a Splunkbase App via CLI

Have you ever needed or wanted to install Splunkbase Apps directly from your unix server/computer without GUI interaction? Please see below:

```javascript
RESPONSE=$(curl -k -XPOST -D - https://splunkbase.splunk.com/api/account:login/ -d 'username=<username>&password=<password'

sid=$(echo "$RESPONSE" | sed -nr "s/.set-cookie: sessionid=([^;]+);./\1/p")

curl --cookie "sessionid=$sid" -L -O -J "http://splunkbase.splunk.com/app/4055/release/4.3.0/download/"
```

From the commands above, please replace the <username> and <password> values with the credentials you use to login at splunk.com (free to create an account). 

Next, replace the url on the 3rd command with the app ID and version # that you would like to download.

