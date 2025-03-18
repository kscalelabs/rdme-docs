# client

KOS client.

## Classes

### KOS

KOS client.

**Arguments:**
- *ip (str, optional)*: IP address of the robot running KOS. Defaults to localhost.
- *port (int, optional)*: Port of the robot running KOS. Defaults to 50051.

- *Attributes*: 
- *imu (IMUServiceClient)*: Client for the IMU service.

#### __aenter__self


#### __aexit__self, exc_type: Any, exc_value: Any, traceback: Any


#### __del__self


#### __enter__self


#### __exit__self, exc_type: Any, exc_value: Any, traceback: Any


#### __init__self, ip: str = "localhost", port: int = 50051


#### actuatorself


#### closeself

Close the gRPC channel.

#### connectself

Connect to the gRPC server and initialize service clients.

#### imuself


#### inferenceself


#### led_matrixself


#### process_managerself


#### simself


#### soundself

