---
title: Introduction to KOS
excerpt: The K-Scale Operating System
deprecated: false
hidden: false
metadata:
  robots: index
---
`pip install pykos`

The K-Scale Operating System (OS) combines the hardware, software and firmware to provide an open-source skeleton for powering general-purpose robots.

[https://github.com/kscalelabs/kos](https://github.com/kscalelabs/kos)

If you need to develop with KOS on your robot, clone the repository and follow the directions on the README.

Here is a high-level overview of the K-Scale OS architecture.

<Image align="center" src="https://files.readme.io/169b02022fcecc9274b804d4d861d4ac097ac3db3f21ce66709eed5851d421c5-Screenshot_2025-01-18_at_01.47.12.png" />

## Simple example

Here is a small example of how to use the Python SDK to interface with kos and control a robot.

```Text python
import pykos
 
kos = pykos.KOS()
 
actuator_id = 1
self.kos.actuator.configure_actuator(actuator_id=actuator_id, kp=120, kd=10, torque_enabled=True)
motor_feedback = kos.actuator.get_actuators_state([actuator_id])
kos.actuator.command_actuators({"actuator_id": actuator_id, "position": 0.5})
```

### Protobufs

The default Protobuf version packaged with apt is quite old, so if you intend to build the SDK from scratch we recommend installing the latest version from here. Here’s an example script for downloading and installing protoc for a Jetson:

```Text python
# Create a temporary directory
mkdir -p /tmp/protoc
cd /tmp/protoc
 
# Download the zip file
wget https://github.com/protocolbuffers/protobuf/releases/download/v29.0/protoc-29.0-linux-aarch_64.zip
 
# Unzip the contents
unzip protoc-29.0-linux-aarch_64.zip
 
# Copy the protoc binary to a directory in your PATH
sudo cp bin/protoc /usr/local/bin/
 
# Copy the protobuf include files
sudo cp -r include/* /usr/local/include/
 
# Clean up
cd ..
rm -rf /tmp/protoc
```