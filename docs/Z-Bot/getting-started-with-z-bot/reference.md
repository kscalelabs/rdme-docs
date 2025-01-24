---
title: PyKOS Reference
excerpt: pykos
deprecated: false
hidden: false
metadata:
  robots: index
---
---
title: PyKOS API Reference
---

# KOS Client

Main client class for interacting with KOS

```python
from pykos import KOS

# Connect to robot
kos = KOS(ip='192.168.1.100', port=50051)
```

### Parameters

* `ip` (str, optional): IP address of robot. Default: 'localhost'
* `port` (int, optional): Port number. Default: 50051

# IMU Methods

## get\_imu\_values

Get the latest IMU sensor values

```python
values = kos.imu.get_imu_values()
```

Returns: `IMUValuesResponse`

## get\_imu\_advanced\_values

Get the latest IMU advanced values

```python
values = kos.imu.get_imu_advanced_values()
```

Returns: `IMUAdvancedValuesResponse`

## get\_euler\_angles

Get the latest Euler angles

```python
angles = kos.imu.get_euler_angles()
```

Returns: `EulerAnglesResponse`

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

### Parameters

* `duration` (float, optional): Duration in seconds. Default: 1.0
* `max_retries` (int, optional): Maximum number of retries
* `max_angular_error` (float, optional): Maximum angular error during zeroing
* `max_velocity` (float, optional): Maximum velocity during zeroing
* `max_acceleration` (float, optional): Maximum acceleration during zeroing

# Actuator Methods

## calibrate

Calibrate an actuator

```python
status = kos.actuator.calibrate(actuator_id=1)
```

### Parameters

* `actuator_id` (int): ID of the actuator to calibrate

Returns: `CalibrationMetadata`

## command\_actuators

Command multiple actuators at once

```python
commands = [
    {'actuator_id': 1, 'position': 90},
    {'actuator_id': 2, 'velocity': 10}
]
response = kos.actuator.command_actuators(commands)
```

### Parameters

* `commands` (list): List of actuator commands. Each command is a dict with:
  * `actuator_id` (int): ID of the actuator
  * `position` (float, optional): Target position
  * `velocity` (float, optional): Target velocity
  * `torque` (float, optional): Target torque

# Types

## IMUResponse

```python
class IMUResponse:
    acceleration: list[float]      # Acceleration values in m/s^2
    angular_velocity: list[float] # Angular velocity values in rad/s
    orientation: list[float]      # Orientation quaternion
```

## ActuatorResponse

```python
class ActuatorResponse:
    position: float  # Current position
    velocity: float  # Current velocity
    torque: float    # Current torque
```

## CalibrationMetadata

```python
class CalibrationMetadata:
    status: str     # Current calibration status
    actuator_id: int  # ID of calibrated actuator
```