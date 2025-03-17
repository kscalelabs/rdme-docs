# actuator

Actuator service client.

## Classes

### `ActuatorCommand (dict)`

dict() -> new empty dictionary\
dict(mapping) -> new dictionary initialized from a mapping object's
(key, value) pairs
dict(iterable) -> new dictionary initialized as if via:
d = {}
for k, v in iterable:
d\[k] = v
dict(\*\*kwargs) -> new dictionary initialized with the name=value pairs
in the keyword argument list.  For example:  dict(one=1, two=2)

### `ActuatorPosition (dict)`

dict() -> new empty dictionary\
dict(mapping) -> new dictionary initialized from a mapping object's
(key, value) pairs
dict(iterable) -> new dictionary initialized as if via:
d = {}
for k, v in iterable:
d\[k] = v
dict(\*\*kwargs) -> new dictionary initialized with the name=value pairs
in the keyword argument list.  For example:  dict(one=1, two=2)

### ActuatorServiceClient (AsyncClientBase)

Client for the ActuatorService.

#### **init**(self, channel: grpc.aio.\_base\_channel.Channel) -> None

#### calibrate(self, actuator\_id: int) -> actuator.CalibrationMetadata

Calibrate an actuator.

#### command\_actuators(self, commands: list\[actuator.ActuatorCommand]) -> kos.actuator\_pb2.CommandActuatorsResponse

Command multiple actuators at once.

Example:

```python
    >>> command_actuators([
    ...     {"actuator_id": 1, "position": 90.0, "velocity": 100.0, "torque": 1.0},
    ...     {"actuator_id": 2, "position": 180.0},
    ... ])

```

**Arguments:**

* *commands*: List of dictionaries containing actuator commands.\
  Each dict should have 'actuator\_id' and optionally 'position',
  'velocity', and 'torque'.

**Returns:**\
List of ActionResult objects indicating success/failure for each command.

#### configure\_actuator(self, \*\*kwargs: Unpack\[actuator.ConfigureActuatorRequest]) -> kos.common\_pb2.ActionResult

Configure an actuator's parameters.

Example:

```python
    >>> configure_actuator(
    ...     actuator_id=1,
    ...     kp=1.0,
    ...     kd=0.1,
    ...     ki=0.01,
    ...     acceleration=2230,
    ...     max_torque=100.0,
    ...     protective_torque=None,
    ...     protection_time=None,
    ...     torque_enabled=True,
    ...     new_actuator_id=None,
    ...     zero_position=True,
    ... )

    >>> configure_actuator(
    ...     actuator_id=2,
    ...     kp=1.0,
    ...     kd=0.1,
    ...     torque_enabled=True,
    ... )

```

**Arguments:**

* *actuator\_id*: ID of the actuator to configure
* \*\**kwargs*: Configuration parameters that may include:\
  kp, kd, ki, max\_torque, protective\_torque,
  protection\_time, torque\_enabled, new\_actuator\_id

**Returns:**\
ActionResponse indicating success/failure

#### get\_actuators\_state(self, actuator\_ids: list\[int] | None = None) -> kos.actuator\_pb2.GetActuatorsStateResponse

Get the state of multiple actuators.

Example:

```python
    >>> get_actuators_state([1, 2])

```

**Arguments:**

* *actuator\_ids*: List of actuator IDs to query. If None, gets state of all actuators.

**Returns:**\
List of ActuatorStateResponse objects containing the state information

#### get\_calibration\_status(self, actuator\_id: int) -> str | None

Get the calibration status of an actuator.

#### move\_to\_position(self, positions: list\[actuator.ActuatorPosition], num\_seconds: float, configure\_actuators: list\[actuator.ConfigureActuatorRequest] | None = None, commands\_per\_second: int = 10, torque\_enabled: bool | None = None) -> None

Helper function for moving actuators to a target position.

This first reads the current position of the actuators, then moves them\
to the target positions at a rate of `commands_per_second` commands per
second.

We can additionally use this command to safely configure the actuator\
PD parameters after setting the target position to the current position.

**Arguments:**

* *positions*: The actuator target positions.
* *num\_seconds*: How long to take the actuators to move to the target\
  positions.
* *configure\_actuators*: List of dictionaries containing actuator\
  configuration parameters.
* *commands\_per\_second*: How many commands to send per second.
* *torque\_enabled*: Whether to enable torque for the actuators.

#### zero\_actuators(self, actuator\_id: int, zero\_position: float, configure\_actuator: actuator.ConfigureActuatorRequest | None = None, target\_velocity: float = 0.25, commands\_per\_second: int = 10, move\_back\_seconds: float = 3.0) -> None

Helper method for zeroing an actuator.

This function works to zero the actuator against an endstop, by moving\
the actuator until it reaches that endstop, then moving it back a small
amount.

We can choose which endstop to zero against by setting the sign of\
`zero_position`. If it is positive, then we rotate counterclockwise
until we reach an endstop, then back by this amount. If it is negative,
then we rotate clockwise until we reach an endstop, then back by this
amount.

**Arguments:**

* *actuator\_id*: The ID of the actuator to zero.
* *zero\_position*: The position to move the actuator back by after\
  reaching the endstop.
* *configure\_actuator*: Configuration parameters to set on the actuator\
  before zeroing.
* *target\_velocity*: The velocity to move the actuator at.
* *commands\_per\_second*: How many commands to send per second.
* *move\_back\_seconds*: How long to move the actuator back by after\
  reaching the endstop.

### ActuatorStateRequest (dict)

dict() -> new empty dictionary\
dict(mapping) -> new dictionary initialized from a mapping object's
(key, value) pairs
dict(iterable) -> new dictionary initialized as if via:
d = {}
for k, v in iterable:
d\[k] = v
dict(\*\*kwargs) -> new dictionary initialized with the name=value pairs
in the keyword argument list.  For example:  dict(one=1, two=2)

### CalibrationMetadata

#### **init**(self, metadata\_any: google.protobuf.any\_pb2.Any) -> None

#### **repr**(self) -> str

#### **str**(self) -> str

#### decode\_metadata(self, metadata\_any: google.protobuf.any\_pb2.Any) -> None

### CalibrationStatus

### ConfigureActuatorRequest (dict)

dict() -> new empty dictionary\
dict(mapping) -> new dictionary initialized from a mapping object's
(key, value) pairs
dict(iterable) -> new dictionary initialized as if via:
d = {}
for k, v in iterable:
d\[k] = v
dict(\*\*kwargs) -> new dictionary initialized with the name=value pairs
in the keyword argument list.  For example:  dict(one=1, two=2)