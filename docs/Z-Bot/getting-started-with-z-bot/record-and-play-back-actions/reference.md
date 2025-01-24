---
title: Reference
deprecated: false
hidden: false
metadata:
  robots: index
---
---
title: PyKOS API Reference
---

# KOS Client

```python
from pykos import KOS

# Connect to robot
kos = KOS(ip='192.168.1.100', port=50051)
```

# IMU Methods

## get\_imu\_values

Get the latest IMU sensor values

```python
values = kos.imu.get_imu_values()
```

Returns: `IMUValuesResponse`

## get\_quaternion

Get the latest quaternion orientation

```python
quat = kos.imu.get_quaternion()
```

Returns: `QuaternionResponse`

## zero

Zero the IMU

```python
# Basic zeroing
kos.imu.zero()

# Advanced zeroing
kos.imu.zero(duration=2.0, max_angular_error=0.1)
```

Parameters:

* `duration` (float, optional): Duration in seconds. Default: 1.0
* `max_retries` (int, optional): Maximum number of retries
* `max_angular_error` (float, optional): Maximum angular error during zeroing

# Actuator Methods

## command\_actuators

Command multiple actuators at once

```python
commands = [
    {'actuator_id': 1, 'position': 90},
    {'actuator_id': 2, 'velocity': 10}
]
response = kos.actuator.command_actuators(commands)
```

Parameters:

* `commands` (list): List of actuator commands

# Types

## IMUResponse

```python
class IMUResponse:
    acceleration: list[float]      # Acceleration values in m/s^2
    angular_velocity: list[float] # Angular velocity values in rad/s
    orientation: list[float]      # Orientation quaternion
```