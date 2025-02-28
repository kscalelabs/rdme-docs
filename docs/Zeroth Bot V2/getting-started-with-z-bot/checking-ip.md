---
title: Connecting to Z-Bot
deprecated: false
hidden: false
metadata:
  robots: index
---
## Obtaining the IP

To check your Z-Bot's IP address, first connect to it through USB and ssh into it. Password is milkv

```Text bash
ssh root@192.168.42.1
```

Once you're in, run `ifconfig` and look for an address that starts with `10.33.xx.yy`

Set up wifi, by navigating to wpa\_supplicant and entering credentials

<Image align="center" width="500px" src="https://files.readme.io/c185e614867a4b23b07fea7a66f852020b867709accb82413f685b4f21850911-Screenshot_2025-01-17_at_4.27.42_PM.png" />

Now you can exit the ssh and start running scripts to control your robot. Put a robot in sarcophagus and run servos/motors with zero calibration:

```Text python
kos.actuator.configure_actuator(ACTUATOR_IDS, kp=32, kd=32, torque_enabled=True, zero_position=True)
```