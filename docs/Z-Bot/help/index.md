---
title: FAQ
deprecated: false
hidden: false
metadata:
  robots: index
---
Main repo: [https://github.com/zeroth-robotics/zeroth-bot](https://github.com/zeroth-robotics/zeroth-bot)

Corresponding gitlab: [https://gitlab.kscale.ai/zeroth-robotics/OpenLCH](https://gitlab.kscale.ai/zeroth-robotics/OpenLCH)

# Flashing Z-Bot

## Basics

### Finding your image

Find the release you want to use: [https://github.com/zeroth-robotics/buildroot/releases](https://github.com/zeroth-robotics/buildroot/releases)

Navigate to the corresponding Gitlab job here (by commit or tag or branch or however you want): [https://gitlab.kscale.ai/zeroth-robotics/OpenLCH-buildroot/-/artifacts](https://gitlab.kscale.ai/zeroth-robotics/OpenLCH-buildroot/-/artifacts)

![](https://files.readme.io/6b5dd1909b146dd853e01f753824024facda14d52c1e6bbaf560d8cf5319a3bc-image.png)

<br />

### Download the artifacts

![](https://files.readme.io/ef80461cce6168f67ced7212f499420c84658482f299a2b143a0ecc4d0a7eb18-image.png)

<br />

### Extract your .img file

![](https://files.readme.io/22bbb1edff4eb30ff0cf84ae49ae811b6a6bbc899717c6321927d33ba2107aed-image.png)

<br />

### Then flash the img onto a micro-SD card using something like BalenaEtcher

![](https://files.readme.io/d91454a31eb1bbbca675339ee48cfcf739ba3e0f79e26b8ca02cef8e80501066-image.png)

<br />

![](https://files.readme.io/57b9cabd7db28e198fec22c250b436bf790d82b089b88184c0945aed0055c403-image.png)

<br />

### And you’re done!

## Optionally

Once you’ve ssh’d into your MilkV over USB (ip = 192.168.42.1)

```bash
ssh root@192.168.42.1

# Copy wpa_supplicant file
cp /etc/wpa_supplicant.conf /boot/

# Add your network
vim /boot/wpa_supplicant.conf
```