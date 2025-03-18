# actuator

Actuator service client.

## Classes

### ActuatorCommand (T, y, p, e, d, D, i, c, t)


### ActuatorPosition (T, y, p, e, d, D, i, c, t)


### ActuatorServiceClient (A, s, y, n, c, C, l, i, e, n, t, B, a, s, e)

Client for the ActuatorService.

#### __init__self, channel: grpc.aio.Channel


#### calibrateself, actuator_id: int

Calibrate an actuator.

#### command_actuatorsself, commands: list[ActuatorCommand]

Command multiple actuators at once.

        Example:
```python
            >>> command_actuators([
            ...     {"actuator_id": 1, "position": 90.0, "velocity": 100.0, "torque": 1.0},
            ...     {"actuator_id": 2, "position": 180.0},
            ... ])

```
**Arguments:**
- *commands*: List of dictionaries containing actuator commands.
                     Each dict should have 'actuator_id' and optionally 'position',
                     'velocity', and 'torque'.

**Returns:**
            List of ActionResult objects indicating success/failure for each command.

#### configure_actuatorself, **kwargs: Unpack[ConfigureActuatorRequest]

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
- *actuator_id*: ID of the actuator to configure
- ***kwargs*: Configuration parameters that may include:
                     kp, kd, ki, max_torque, protective_torque,
                     protection_time, torque_enabled, new_actuator_id

**Returns:**
            ActionResponse indicating success/failure

#### get_actuators_stateself,
        actuator_ids: list[int] | None = None,

Get the state of multiple actuators.

        Example:
```python
            >>> get_actuators_state([1, 2])

```
**Arguments:**
- *actuator_ids*: List of actuator IDs to query. If None, gets state of all actuators.

**Returns:**
            List of ActuatorStateResponse objects containing the state information

#### get_calibration_statusself, actuator_id: int

Get the calibration status of an actuator.

#### move_to_positionself,
        positions: list[ActuatorPosition],
        num_seconds: float,
        configure_actuators: list[ConfigureActuatorRequest] | None = None,
        commands_per_second: int = 10,
        torque_enabled: bool | None = None,

Helper function for moving actuators to a target position.

        This first reads the current position of the actuators, then moves them
        to the target positions at a rate of `commands_per_second` commands per
        second.

        We can additionally use this command to safely configure the actuator
        PD parameters after setting the target position to the current position.

**Arguments:**
- *positions*: The actuator target positions.
- *num_seconds*: How long to take the actuators to move to the target
                positions.
- *configure_actuators*: List of dictionaries containing actuator
                configuration parameters.
- *commands_per_second*: How many commands to send per second.
- *torque_enabled*: Whether to enable torque for the actuators.

#### zero_actuatorsself,
        actuator_id: int,
        zero_position: float,
        configure_actuator: ConfigureActuatorRequest | None = None,
        target_velocity: float = 0.25,
        commands_per_second: int = 10,
        move_back_seconds: float = 3.0,

Helper method for zeroing an actuator.

        This function works to zero the actuator against an endstop, by moving
        the actuator until it reaches that endstop, then moving it back a small
        amount.

        We can choose which endstop to zero against by setting the sign of
        `zero_position`. If it is positive, then we rotate counterclockwise
        until we reach an endstop, then back by this amount. If it is negative,
        then we rotate clockwise until we reach an endstop, then back by this
        amount.

**Arguments:**
- *actuator_id*: The ID of the actuator to zero.
- *zero_position*: The position to move the actuator back by after
                reaching the endstop.
- *configure_actuator*: Configuration parameters to set on the actuator
                before zeroing.
- *target_velocity*: The velocity to move the actuator at.
- *commands_per_second*: How many commands to send per second.
- *move_back_seconds*: How long to move the actuator back by after
                reaching the endstop.

### ActuatorStateRequest (T, y, p, e, d, D, i, c, t)


### CalibrationMetadata


#### __init__self, metadata_any: AnyPb2


#### __repr__self


#### __str__self


#### decode_metadataself, metadata_any: AnyPb2


### CalibrationStatus


### ConfigureActuatorRequest (T, y, p, e, d, D, i, c, t)
