# imu

IMU service client.

## Classes

### CalibrationMetadata


#### __init__(self, metadata_any: google.protobuf.any_pb2.Any) -> None


#### __repr__(self) -> str


#### __str__(self) -> str


#### decode_metadata(self, metadata_any: google.protobuf.any_pb2.Any) -> None


### CalibrationStatus


### IMUServiceClient (AsyncClientBase)

Client for the IMUService.

#### __init__(self, channel: grpc.aio._base_channel.Channel) -> None


#### calibrate(self) -> kos.imu_pb2.CalibrateIMUResponse

Calibrate the IMU.

This starts a long-running calibration operation. The operation can be monitored
using get_calibration_status().

**Returns:**
    CalibrationMetadata: Metadata about the calibration operation.

#### get_euler_angles(self) -> kos.imu_pb2.EulerAnglesResponse

Get the latest Euler angles.

**Returns:**
    EulerAnglesResponse: The latest Euler angles.

#### get_imu_advanced_values(self) -> kos.imu_pb2.IMUAdvancedValuesResponse

Get the latest IMU advanced values.

**Returns:**
    ImuAdvancedValuesResponse: The latest IMU advanced values.

#### get_imu_values(self) -> kos.imu_pb2.IMUValuesResponse

Get the latest IMU sensor values.

**Returns:**
    ImuValuesResponse: The latest IMU sensor values.

#### get_quaternion(self) -> kos.imu_pb2.QuaternionResponse

Get the latest quaternion.

**Returns:**
    QuaternionResponse: The latest quaternion.

#### zero(self, duration: float = 1.0, **kwargs: Unpack[imu.ZeroIMURequest]) -> kos.common_pb2.ActionResponse

Zero the IMU.

Example:
```python
    >>> await zero(duration=1.0,
    ...     max_retries=3,
    ...     max_angular_error=1.0,
    ...     max_velocity=1.0,
    ...     max_acceleration=1.0
    ... )

```
**Arguments:**
- *duration*: Duration in seconds for zeroing operation
- ***kwargs*: Additional zeroing parameters that may include:
- *max_retries*: Maximum number of retries
- *max_angular_error*: Maximum angular error during zeroing
- *max_velocity*: Maximum velocity during zeroing
- *max_acceleration*: Maximum acceleration during zeroing

**Returns:**
    ActionResponse: The response from the zero operation.

### ZeroIMURequest (dict)

dict() -> new empty dictionary
dict(mapping) -> new dictionary initialized from a mapping object's
    (key, value) pairs
dict(iterable) -> new dictionary initialized as if via:
    d = {}
    for k, v in iterable:
        d[k] = v
dict(**kwargs) -> new dictionary initialized with the name=value pairs
    in the keyword argument list.  For example:  dict(one=1, two=2)
