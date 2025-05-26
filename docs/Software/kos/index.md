---
title: K-OS
excerpt: Overview of the K-Scale Operating System architecture
deprecated: false
hidden: false
metadata:
  robots: index
---
The [K-Scale Operating System](https://github.com/kscalelabs/kos)  combines the hardware, software and firmware for K-Scale's general-purpose robots. To install the Python client for interacting with the OS, run the following command:

```shell
pip install pykos
```

Here is a high-level overview of the K-Scale OS architecture.

<Image align="center" src="https://files.readme.io/169b02022fcecc9274b804d4d861d4ac097ac3db3f21ce66709eed5851d421c5-Screenshot_2025-01-18_at_01.47.12.png" />

<br />

### KOS Setup

1. Clone the kos-kbot library onto the robot head's compute

   `git clone https://github.com/kscalelabs/kos-kbot.git`
2. Setup Rust Cargo etc. on the Raspberry Pi
3. Edit the `/src/lib.rs` file to remove the leg actuator id if they are not present

   [https://github.com/kscalelabs/kos-kbot/blob/00fea353dd058a4d84c6897bfc27fde92c165f6e/src/lib.rs#L370](https://github.com/kscalelabs/kos-kbot/blob/00fea353dd058a4d84c6897bfc27fde92c165f6e/src/lib.rs#L370)
4. Start the server with `cargo run --release` you can now use pykos. If running pykos on a different device, make sure the ip is pointed to the right one. By default, it uses `0.0.0.0`ie localhost (same device).