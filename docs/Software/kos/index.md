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

<br />

### Example Usage

The first step on receiving the prototype k-bot is to check the zeros. You can do this once installing `pykos` using the following command. Check the K-Bot section of the doc and make sure the CAN lines are connected to the CAN board and the usb c from the CAN board is plugging into the head.

You can also find the out-of-box actuator id to where the motor is on the K-Bot section of this doc.

<br />

**Read Motor**

```python
import pykos
import asyncio

async def main():
    async with pykos.KOS(0.0.0.0) as kos:
        print(await kos.actuator.get_actuators_state([25])) #for actuator ID 25

if __name__ == "__main__":
    asyncio.run(main())

```

<br />

**Set Zero in Current Place**

```python
import asyncio
import pykos

async def main():
    async with pykos.KOS() as kos:
        # for id in range(60):
            try:
                await kos.actuator.configure_actuator(actuator_id=id, torque_enabled=False, zero_position=True)
            except Exception as e:
                print(f"Failed to configure actuator {id}")

if __name__ == "__main__":
    asyncio.run(main())

```

<br />

**Move Motor**

Controlling the actuator is as follows:

```python
import pykos
import asyncio

async def main():
    async with pykos.KOS() as kos:
        await kos.actuator.configure_actuator(actuator_id=13, kp=10, kd=1, torque_enabled=True)

        //

        await kos.actuator.command_actuators([{'actuator_id': id, 'position': -10}])

if __name__ == "__main__":
    asyncio.run(main())
```

<br />

The actuator we use are Robstride actuator: [https://github.com/RobStride/Product\_Information](https://github.com/RobStride/Product_Information). The control mode we use is the 'Operation control mode' which is described at the end of the manual. Thus, we can also pass in an expected velocity as such:

```python
import pykos
import asyncio

async def main():
    async with pykos.KOS() as kos:
        await kos.actuator.configure_actuator(actuator_id=13, kp=10, kd=1, torque_enabled=True)

        //

        await kos.actuator.command_actuators([{'actuator_id': id, 'velocity':10.0, 'position': -10}])

if __name__ == "__main__":
    asyncio.run(main())
```