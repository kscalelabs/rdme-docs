---
title: FAQ
deprecated: false
hidden: false
metadata:
  robots: index
---
Main repo: [https://github.com/zeroth-robotics/zeroth-bot](https://github.com/zeroth-robotics/zeroth-bot)

Corresponding gitlab: [https://gitlab.kscale.ai/zeroth-robotics/OpenLCH](https://gitlab.kscale.ai/zeroth-robotics/OpenLCH)

<br />

## Optionally

Once you’ve ssh’d into your MilkV over USB (ip = 192.168.42.1)

```bash
ssh root@192.168.42.1

# Copy wpa_supplicant file
cp /etc/wpa_supplicant.conf /boot/

# Add your network
vim /boot/wpa_supplicant.conf
```