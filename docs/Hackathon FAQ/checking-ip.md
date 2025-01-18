---
title: Connecting to Z-Bot
deprecated: false
hidden: false
metadata:
  robots: index
---
To check your Z-Bot's IP address, first connect to it through USB and ssh into it

```Text bash
ssh root@192.168.42.1
```

Once you're in, run `ifconfig` and look for an address that starts with `10.33.xx.yy`