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

#### __aenter__(self) -> 'KOS'


#### __aexit__(self, exc_type: Any, exc_value: Any, traceback: Any) -> None


#### __del__(self) -> None


#### __enter__(self) -> 'KOS'


#### __exit__(self, exc_type: Any, exc_value: Any, traceback: Any) -> None


#### __init__(self, ip: str = 'localhost', port: int = 50051) -> None


#### close(self) -> None

Close the gRPC channel.

#### connect(self) -> None

Connect to the gRPC server and initialize service clients.
