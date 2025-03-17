---
title: client
---

# client

#### Help on module client


NAME
    client - KOS client.

CLASSES
    builtins.object
        KOS

    class KOS(builtins.object)
     |  KOS(ip: str = 'localhost', port: int = 50051) -> None
     |
     |  KOS client.
     |
     |  Args:
     |      ip (str, optional): IP address of the robot running KOS. Defaults to localhost.
     |      port (int, optional): Port of the robot running KOS. Defaults to 50051.
     |
     |  Attributes:
     |      imu (IMUServiceClient): Client for the IMU service.
     |
     |  Methods defined here:
     |
     |  async __aenter__(self) -> 'KOS'
     |
     |  async __aexit__(self, exc_type: Any, exc_value: Any, traceback: Any) -> None
     |
     |  __del__(self) -> None
     |
     |  __enter__(self) -> 'KOS'
     |
     |  __exit__(self, exc_type: Any, exc_value: Any, traceback: Any) -> None
     |
     |  __init__(self, ip: str = 'localhost', port: int = 50051) -> None
     |      Initialize self.  See help(type(self)) for accurate signature.
     |
     |  async close(self) -> None
     |      Close the gRPC channel.
     |
     |  connect(self) -> None
     |      Connect to the gRPC server and initialize service clients.
     |
     |  ----------------------------------------------------------------------
     |  Readonly properties defined here:
     |
     |  actuator
     |
     |  imu
     |
     |  inference
     |
     |  led_matrix
     |
     |  process_manager
     |
     |  sim
     |
     |  sound
     |
     |  ----------------------------------------------------------------------
     |  Data descriptors defined here:
     |
     |  __dict__
     |      dictionary for instance variables
     |
     |  __weakref__
     |      list of weak references to the object

FILE
    /Users/verdakorzeniewski/kscale/kos/kos-py/pykos/client.py



