# KOS Python API

Welcome to the KOS (K-Scale Operating System) Python API documentation. This API allows you to interact with robots and devices running the KOS system.

## Overview

KOS provides a unified interface to various hardware components and services, making it easy to control robots, access sensors, and run machine learning models. The Python API is built on top of gRPC, providing asynchronous access to all KOS services.

## Key Features

- **Asynchronous API**: All operations are non-blocking, allowing for efficient concurrent operations
- **Service-Oriented Architecture**: Access different hardware components through dedicated service clients
- **Easy Connection Management**: Simple connection handling with context manager support
- **Comprehensive Hardware Support**: Actuators, IMU, LED matrix, sound, and more
- **ML Model Inference**: Deploy and run neural networks directly on the device
- **Simulation Support**: Test your code in simulation before running on hardware

## Getting Started

### Installation

```bash
pip install pykos
```

### Basic Usage

```python
import asyncio
from pykos import KOS

async def main():
    # Connect to a KOS device
    async with KOS("192.168.1.100") as kos:
        # Get the IMU service client
        imu = kos.imu()
        
        # Get the current orientation
        orientation = await imu.get_orientation()
        print(f"Roll: {orientation.roll}°, Pitch: {orientation.pitch}°, Yaw: {orientation.yaw}°")
        
        # Control an actuator
        actuator = kos.actuator()
        await actuator.command_actuators([
            {"actuator_id": 1, "position": 90.0}
        ])

asyncio.run(main())
```

## Available Services

KOS provides the following services:

- **Actuator Service**: Control motors and servos
- **IMU Service**: Access orientation, acceleration, and angular velocity
- **LED Matrix Service**: Control LED matrix displays
- **Sound Service**: Play and record audio
- **Process Manager Service**: Monitor system resources and processes
- **Inference Service**: Run machine learning models
- **Simulation Service**: Test in virtual environments

## Example Projects

Here are some example projects showing how to use the KOS Python API:

### Orientation Display

```python
import asyncio
from pykos import KOS

async def main():
    async with KOS() as kos:
        imu = kos.imu()
        led = kos.led_matrix()
        
        while True:
            # Get orientation
            orientation = await imu.get_orientation()
            
            # Display the roll angle on the LED matrix
            await led.draw_text(
                f"Roll: {orientation.roll:.1f}°",
                color=[0, 255, 0],  # Green text
                scroll=True
            )
            
            # Update at 2Hz
            await asyncio.sleep(0.5)

asyncio.run(main())
```

### Gesture Detection

```python
import asyncio
import numpy as np
from pykos import KOS

async def main():
    async with KOS() as kos:
        imu = kos.imu()
        sound = kos.sound()
        
        # Keep track of acceleration history
        accel_history = []
        
        while True:
            # Get acceleration data
            accel = await imu.get_acceleration()
            accel_history.append((accel.x, accel.y, accel.z))
            
            # Keep only the last 20 samples
            if len(accel_history) > 20:
                accel_history.pop(0)
            
            # Calculate acceleration magnitude
            magnitudes = [np.sqrt(x**2 + y**2 + z**2) for x, y, z in accel_history]
            
            # Check for a "shake" gesture
            if len(magnitudes) >= 10:
                avg_mag = np.mean(magnitudes)
                if avg_mag > 15.0:  # Threshold for shake detection
                    print("Shake detected!")
                    await sound.play_tone(frequency=880, duration_ms=200)
                    accel_history = []  # Reset history after detection
            
            await asyncio.sleep(0.05)  # Sample at 20Hz

asyncio.run(main())
```

## Contents

- [Client Documentation](./client)
- [Services](./services/index)