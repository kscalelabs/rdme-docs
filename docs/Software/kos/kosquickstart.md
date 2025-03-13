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

Running on Robot

```bash
mkdir local_crates
cd local_crates
git clone -b parse-faults https://github.com/kscalelabs/actuator.git
```

`conda create -n kos-kbot_env_name python=3.11`

`conda activate kos-kbot_env_name`

`pip install numpy scipy pygame kinfer==0.0.5 pykos`

```bash
cargo run --release
```

KOS is now listening

*telemetry*

on the same device, new terminal

```bash
mosquitto_sub -t '#' > today_date.txt
```

<br />

### CLIENT

write python code to interact with it, like

[https://github.com/kscalelabs/kbot-unit-tests](https://github.com/kscalelabs/kbot-unit-tests)

waveform test: [https://github.com/kscalelabs/tests](https://github.com/kscalelabs/tests)

```python
from pykos import KOS
```

```python
async with KOS(ip=args.host, port=args.port) as sim_kos, \
	         KOS(ip="100.89.14.31", port=args.port) as real_kos:
	  await sim_kos.sim.reset()
	  await configure_robot(sim_kos)
	  await configure_robot(real_kos)
	  print("Homing...")
	  homing_command = [{
	      "actuator_id": actuator.actuator_id,
	      "position": 0.0
	  } for actuator in ACTUATOR_LIST]
	  await asyncio.gather(
	      sim_kos.actuator.command_actuators(homing_command),
	      real_kos.actuator.command_actuators(homing_command),
	  )
	  await asyncio.sleep(2)
```