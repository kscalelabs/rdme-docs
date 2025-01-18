---
title: Connecting to your Z-Bot
excerpt: Connecting to your Z-Bot on the K-Scale network
deprecated: false
hidden: false
metadata:
  robots: index
---
On the K-Scale network, you can connect to your Z-Bot using the name on the back of your bot

Plug in your robot.

After around 20 seconds, you can `ping` the bot using the ID portion of the name on the back

Connecting to `Z-9 Wesley`:

```text bash
$ ping Z-9

PING z-9.kscale.lan (10.33.85.9): 56 data bytes
64 bytes from 10.33.85.9: icmp_seq=0 ttl=64 time=99.295 ms
64 bytes from 10.33.85.9: icmp_seq=1 ttl=64 time=8.524 ms
64 bytes from 10.33.85.9: icmp_seq=2 ttl=64 time=3.600 ms
64 bytes from 10.33.85.9: icmp_seq=3 ttl=64 time=7.204 ms
64 bytes from 10.33.85.9: icmp_seq=4 ttl=64 time=4.088 ms
64 bytes from 10.33.85.9: icmp_seq=5 ttl=64 time=8.216 ms
^C
--- z-9.kscale.lan ping statistics ---
6 packets transmitted, 6 packets received, 0.0% packet loss
round-trip min/avg/max/stddev = 3.600/21.821/99.295/34.699 ms
```