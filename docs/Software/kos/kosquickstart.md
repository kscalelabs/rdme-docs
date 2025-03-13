---
title: K-Bot KOS Quick Start
deprecated: false
hidden: false
metadata:
  robots: index
---
### Servers

**Sim**

```shell
pip install kos-sim  # To install the simulation server
kos-sim kbot-v1 --no-gravity --no-render
```

This will create a gRPC server which listens for KOS commands and replicates them on your robot.

**K-Bot**

Set up CAN lines to communicate with actuators.

```bash
#!/bin/bash

for i in {0..4} 	
	do echo "Setting up can$i..." 	
	sudo ip link set can$i down 	
	sudo ip link set can$i type can bitrate 1000000 	
	sudo ip link set can$i txqueuelen 1000 	
	sudo ip link set can$i up 
done
```

To run KOS on the K-Bot, use the commands:

```bash
# Use this if you want the bleeding edge actuator package.
mkdir local_crates
cd local_crates
git clone -b parse-faults https://github.com/kscalelabs/actuator.git

# Runs KOS
cargo run --release
```

You can read telemetry from Mosquitto:

```bash
mosquitto_sub -t '#' > today_date.txt
```

### Client

We have a set of unit tests which you can run on the K-Bot [here](https://github.com/kscalelabs/kbot-unit-tests) .