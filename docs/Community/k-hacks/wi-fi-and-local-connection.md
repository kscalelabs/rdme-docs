---
title: Wi-Fi and local connection
deprecated: false
hidden: false
metadata:
  robots: index
---
All of the hackathon Z-Bots have a numeric ID written on the back, e.g. "Z-4 Denys".

To connect to your teams Z-Bot using pykos, you would either use local USB connection

```
import pykos
KOS = pykos.KOS('192.168.42.1')  # this ip is static
```

Or the domain name of the robot on the khacks wifi

```
import pykos
KOS = pykos.KOS('Z-4.kscale.lan')  # Or 10.33.85.4, where last digit is robot ID
```

Wi-Fi is `khacks` and password is `khacks++`