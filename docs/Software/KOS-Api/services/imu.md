# imu

IMU service client.

## Classes

### CalibrationMetadata


#### __init__self, metadata_any: AnyPb2


#### __repr__self


#### __str__self


#### decode_metadataself, metadata_any: AnyPb2


### CalibrationStatus


### IMUServiceClient (A, s, y, n, c, C, l, i, e, n, t, B, a, s, e)

Client for the IMUService.

#### __init__self, channel: grpc.aio.Channel


#### calibrateself

Calibrate the IMU.

        This starts a long-running calibration operation. The operation can be monitored
        using get_calibration_status().

**Returns:**
            CalibrationMetadata: Metadata about the calibration operation.

#### get_euler_anglesself

Get the latest Euler angles.

**Returns:**
            EulerAnglesResponse: The latest Euler angles.

#### get_imu_advanced_valuesself

Get the latest IMU advanced values.

**Returns:**
            ImuAdvancedValuesResponse: The latest IMU advanced values.

#### get_imu_valuesself

Get the latest IMU sensor values.

**Returns:**
            ImuValuesResponse: The latest IMU sensor values.

#### get_quaternionself

Get the latest quaternion.

**Returns:**
            QuaternionResponse: The latest quaternion.

#### zeroself, duration: float = 1.0, **kwargs: Unpack[ZeroIMURequest]

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

### ZeroIMURequest (T, y, p, e, d, D, i, c, t)


## Functions

### _duration_from_secondsseconds: float

Convert seconds to Duration proto.
