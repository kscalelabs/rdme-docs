# IMU Service

The IMU (Inertial Measurement Unit) Service provides access to orientation, acceleration, and angular velocity data.

## Classes

### ZeroIMURequest (TypedDict)

Configuration parameters for IMU zeroing operation.

#### Fields

- **max_retries**: NotRequired[int] - Maximum number of retries for zeroing operation
- **max_angular_error**: NotRequired[float] - Maximum allowable angular error in degrees
- **max_velocity**: NotRequired[float] - Maximum allowable angular velocity in degrees/second
- **max_acceleration**: NotRequired[float] - Maximum allowable acceleration in m/s²

### CalibrationStatus

Constants used for representing IMU calibration status.

#### Fields

- **Calibrating**: "calibrating" - Calibration is in progress
- **Calibrated**: "calibrated" - Calibration completed successfully
- **Timeout**: "timeout" - Calibration timed out

### CalibrationMetadata

Metadata for IMU calibration operations.

#### Methods

##### `__init__(self, metadata_any: AnyPb2)`

Initialize the calibration metadata from a protobuf Any message.

##### `decode_metadata(self, metadata_any: AnyPb2)`

Decode metadata from protobuf Any message and update class attributes.

##### `__str__(self)`

String representation of calibration metadata.

##### `__repr__(self)`

Representation of calibration metadata.

### IMUServiceClient (AsyncClientBase)

Client for interacting with the IMU Service.

#### Methods

##### `__init__(self, channel: grpc.aio.Channel)`

Initialize the IMU service client with a gRPC channel.

##### `get_orientation(self) -> OrientationData`

Get the current orientation of the device.

**Returns:**
- OrientationData containing current orientation information including:
  - roll (float): Rotation around the X axis in degrees
  - pitch (float): Rotation around the Y axis in degrees
  - yaw (float): Rotation around the Z axis in degrees
  - quaternion (list[float]): Orientation as a quaternion [w, x, y, z]

**Example:**
```python
orientation = await imu_client.get_orientation()
print(f"Current roll: {orientation.roll} degrees")
print(f"Current pitch: {orientation.pitch} degrees")
print(f"Current yaw: {orientation.yaw} degrees")
```

##### `get_acceleration(self) -> AccelerationData`

Get the current acceleration data from the IMU.

**Returns:**
- AccelerationData containing linear acceleration in m/s² along the X, Y, and Z axes

**Example:**
```python
accel = await imu_client.get_acceleration()
print(f"X acceleration: {accel.x} m/s²")
print(f"Y acceleration: {accel.y} m/s²")
print(f"Z acceleration: {accel.z} m/s²")
```

##### `get_angular_velocity(self) -> AngularVelocityData`

Get the current angular velocity data from the IMU.

**Returns:**
- AngularVelocityData containing rotation rates in degrees per second around the X, Y, and Z axes

**Example:**
```python
angular_vel = await imu_client.get_angular_velocity()
print(f"X rotation rate: {angular_vel.x} deg/s")
print(f"Y rotation rate: {angular_vel.y} deg/s")
print(f"Z rotation rate: {angular_vel.z} deg/s")
```

##### `get_imu_state(self) -> IMUState`

Get the complete IMU state including orientation, acceleration, and angular velocity in a single call.

**Returns:**
- IMUState containing:
  - orientation (OrientationData): Current orientation data
  - acceleration (AccelerationData): Current acceleration data
  - angular_velocity (AngularVelocityData): Current angular velocity data

**Example:**
```python
state = await imu_client.get_imu_state()
print(f"Roll: {state.orientation.roll} degrees")
print(f"X acceleration: {state.acceleration.x} m/s²")
print(f"Z angular velocity: {state.angular_velocity.z} deg/s")
```

##### `calibrate(self) -> CalibrationMetadata`

Start calibration of the IMU. This is an asynchronous operation.

**Returns:**
- CalibrationMetadata: Metadata about the calibration operation

**Notes:**
- Calibration requires the device to be stationary and level
- Check calibration status with `get_calibration_status()`

##### `get_calibration_status(self) -> str | None`

Get the current status of an IMU calibration operation.

**Returns:**
- String indicating calibration status: "calibrating", "calibrated", "timeout", or None if not available

##### `zero_imu(self, **kwargs: Unpack[ZeroIMURequest]) -> ActionResult`

Zero the IMU orientation by resetting the current position as the reference orientation.

**Parameters:**
- **kwargs: Configuration parameters for zeroing (see ZeroIMURequest fields)

**Returns:**
- ActionResult indicating success/failure

**Example:**
```python
result = await imu_client.zero_imu(
    max_retries=3,
    max_angular_error=0.5,
    max_velocity=0.1
)
```