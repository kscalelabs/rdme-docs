# ActuatorService

The Actuator Service provides control over physical actuators, allowing precise motion control, calibration, and configuration.

## Classes

### ActuatorCommand (TypedDict)

Dictionary for sending actuator commands.

#### Fields

- **actuator_id**: int - Unique identifier for the actuator
- **position**: NotRequired[float] - Target position (in degrees)
- **velocity**: NotRequired[float] - Velocity limit (in degrees/second)
- **torque**: NotRequired[float] - Torque limit (in Nm)

### ActuatorPosition (TypedDict)

Dictionary for target actuator position.

#### Fields

- **actuator_id**: int - Unique identifier for the actuator
- **position**: float - Target position (in degrees)

### ConfigureActuatorRequest (TypedDict)

Dictionary for actuator configuration parameters.

#### Fields

- **actuator_id**: int - Unique identifier for the actuator to configure
- **kp**: NotRequired[float] - Position gain (proportional gain)
- **kd**: NotRequired[float] - Velocity gain (derivative gain)
- **ki**: NotRequired[float] - Integral gain
- **acceleration**: NotRequired[float] - Acceleration limit (in degrees/second²)
- **max_torque**: NotRequired[float] - Maximum torque limit (in Nm)
- **protective_torque**: NotRequired[float] - Protective torque threshold (in Nm)
- **protection_time**: NotRequired[float] - Protection timeout (in seconds)
- **torque_enabled**: NotRequired[bool] - Enable/disable actuator torque
- **new_actuator_id**: NotRequired[int] - New ID to assign to the actuator
- **zero_position**: NotRequired[bool] - Reset the zero position

### ActuatorStateRequest (TypedDict)

Dictionary for requesting actuator state.

#### Fields

- **actuator_ids**: list[int] - List of actuator IDs to query

### CalibrationStatus

Constants used for representing actuator calibration status.

#### Fields

- **Calibrating**: "calibrating" - Calibration is in progress
- **Calibrated**: "calibrated" - Calibration completed successfully
- **Timeout**: "timeout" - Calibration timed out

### CalibrationMetadata

Metadata for actuator calibration operations.

#### Methods

##### `__init__(self, metadata_any: AnyPb2)`

Initialize the calibration metadata from a protobuf Any message.

##### `decode_metadata(self, metadata_any: AnyPb2)`

Decode metadata from protobuf Any message and update class attributes.

##### `__str__(self)`

String representation of calibration metadata.

##### `__repr__(self)`

Representation of calibration metadata.

### ActuatorServiceClient (AsyncClientBase)

Client for interacting with the Actuator Service.

#### Methods

##### `__init__(self, channel: grpc.aio.Channel)`

Initialize the actuator service client with a gRPC channel.

##### `calibrate(self, actuator_id: int) -> CalibrationMetadata`

Start calibration of an actuator. This is an asynchronous operation.

**Parameters:**
- actuator_id: ID of the actuator to calibrate

**Returns:**
- CalibrationMetadata: Metadata about the calibration operation

##### `get_calibration_status(self, actuator_id: int) -> str | None`

Get the current status of a calibration operation.

**Parameters:**
- actuator_id: ID of the actuator to check

**Returns:**
- String indicating calibration status or None if not available

##### `command_actuators(self, commands: list[ActuatorCommand]) -> CommandActuatorsResponse`

Command multiple actuators at once with different parameters.

**Example:**
```python
command_actuators([
    {"actuator_id": 1, "position": 90.0, "velocity": 100.0, "torque": 1.0},
    {"actuator_id": 2, "position": 180.0},
])
```

**Parameters:**
- commands: List of dictionaries containing actuator commands.
  Each dict should have 'actuator_id' and optionally 'position',
  'velocity', and 'torque'.

**Returns:**
- Response containing success/failure for each command

##### `configure_actuator(self, **kwargs: Unpack[ConfigureActuatorRequest]) -> ActionResult`

Configure parameters for a specific actuator.

**Example:**
```python
configure_actuator(
    actuator_id=1,
    kp=1.0,
    kd=0.1,
    ki=0.01,
    acceleration=2230,
    max_torque=100.0,
    torque_enabled=True,
    zero_position=True
)
```

**Parameters:**
- actuator_id: ID of the actuator to configure
- **kwargs: Configuration parameters (see ConfigureActuatorRequest fields)

**Returns:**
- ActionResult indicating success/failure

##### `get_actuators_state(self, actuator_ids: list[int] | None = None) -> GetActuatorsStateResponse`

Get the current state of one or more actuators.

**Example:**
```python
state = get_actuators_state([1, 2])
print(f"Actuator 1 position: {state.states[0].position}")
```

**Parameters:**
- actuator_ids: List of actuator IDs to query. If None, gets state of all actuators.

**Returns:**
- Response containing state information for each requested actuator

##### `move_to_position(self, positions: list[ActuatorPosition], num_seconds: float, configure_actuators: list[ConfigureActuatorRequest] | None = None, commands_per_second: int = 10, torque_enabled: bool | None = None) -> None`

Move actuators to target positions smoothly over a specified time period.

**Example:**
```python
await actuator_client.move_to_position(
    positions=[
        {"actuator_id": 1, "position": 90.0},
        {"actuator_id": 2, "position": 45.0}
    ],
    num_seconds=2.0
)
```

**Parameters:**
- positions: List of target positions for each actuator
- num_seconds: Time to complete the movement (in seconds)
- configure_actuators: Optional list of configuration parameters to apply before moving
- commands_per_second: Frequency of command updates during the motion
- torque_enabled: Whether to enable torque before moving
