---
title: Start building with KOS
excerpt: Learn to develop and control K-Scale robots with our open-source software.
deprecated: false
hidden: false
metadata:
  robots: index
next:
  pages:
    - slug: set-up-your-environment
      title: Set up your environment
      type: basic
    - slug: build-and-test-skills
      title: Building and testing skills
      type: basic
---
## Introduction

`pykos` is a Python client for the K-Scale Operating System (KOS), allowing you to interact with various services provided by KOS, such as controlling actuators, accessing IMU data, managing processes, and more.

## Installation

To install `pykos`, you can use pip:

```shell
pip install pykos
```

## Getting Started

First, import the `pykos` module and create an instance of the KOS client:

```python
from pykos import KOS

# Connect to KOS running on localhost at port 50051
client = KOS(ip='localhost', port=50051)
```

<br />

## Services

The KOS client provides several services, each accessible via the client object. Below are the services and examples of how to use them.

<br />

### Actuator Service

Control actuators connected to the robot.

#### Example: Configure an Actuator

```python
# Configure actuator with ID 1
response = client.actuator.configure_actuator(
    actuator_id=1,
    kp=1.0,
    kd=0.1,
    ki=0.01,
    max_torque=100.0,
    torque_enabled=True,
    zero_position=True
)
if response.success:
    print("Actuator configured successfully.")
else:
    print(f"Failed to configure actuator: {response.error}")
```

<br />

#### Example: Command

```python
# Command multiple actuators
commands = [
    {"actuator_id": 1, "position": 90.0},
    {"actuator_id": 2, "position": 180.0}
]
response = client.actuator.command_actuators(commands)
for result in response.results:
    if result.success:
        print(f"Actuator {result.actuator_id} commanded successfully.")
    else:
        print(f"Failed to command actuator {result.actuator_id}: {result.error}")
```

<br />

### IMU Service

Access the Inertial Measurement Unit (IMU) data.

#### Example: Get IMU Values

```python
# Get basic IMU sensor values
imu_values = client.imu.get_imu_values()
print(f"Accelerometer X: {imu_values.accel_x}")
print(f"Gyroscope Z: {imu_values.gyro_z}")
```

#### Example: Zero the IMU

```python
# Zero the IMU with default parameters
response = client.imu.zero(duration=1.0)
if response.success:
    print("IMU zeroed successfully.")
else:
    print(f"Failed to zero IMU: {response.error}")
```

<br />

### LED Matrix Service

Control an LED matrix display.

#### Example: Get Matrix Info

```python
# Get LED matrix information
matrix_info = client.led_matrix.get_matrix_info()
print(f"Matrix size: {matrix_info.width} x {matrix_info.height}")
```

<br />

#### Example: Write to the LED Matrix

```python
# Create a buffer to turn all LEDs on
buffer_size = (matrix_info['width'] * matrix_info['height']) // 8
buffer = bytes([0xFF] * buffer_size)

# Write buffer to the LED matrix
response = client.led_matrix.write_buffer(buffer)
if response.success:
    print("LED matrix updated successfully.")
else:
    print(f"Failed to update LED matrix: {response.error}")
```

<br />

### Sound Service

Play and record audio.

#### Example: Get Audio Info

```python
# Get audio capabilities
audio_info = client.sound.get_audio_info()
print(f"Playback available: {audio_info['playback']['available']}")
print(f"Supported sample rates: {audio_info['playback']['sample_rates']}")
```

#### Example: Play Audio

```python
# Play a raw audio file
def audio_chunks():
    with open('audio.raw', 'rb') as f:
        while True:
            chunk = f.read(4096)
            if not chunk:
                break
            yield chunk

audio_config = {
    "sample_rate": 44100,
    "bit_depth": 16,
    "channels": 2
}
response = client.sound.play_audio(audio_chunks(), **audio_config)
if response.success:
    print("Audio played successfully.")
else:
    print(f"Failed to play audio: {response.error}")
```

<br />

### Process Manager Service

Manage processes on the robot.

#### Example: Start KClip Recording

```python
# Start KClip recording with an action
response = client.process_manager.start_kclip(action="wave")
if response.success:
    print(f"KClip recording started. Clip UUID: {response.clip_uuid}")
else:
    print(f"Failed to start KClip recording: {response.error}")
```

#### Example: Stop KClip Recording

```python
# Stop KClip recording
response = client.process_manager.stop_kclip()
if response.success:
    print(f"KClip recording stopped. Clip UUID: {response.clip_uuid}")
else:
    print(f"Failed to stop KClip recording: {response.error}")
```

### Inference Service

Upload models and perform inference.

#### Example: Upload a Model

```python
# Upload a model file
with open('model.bin', 'rb') as f:
    model_data = f.read()

metadata = {
    "model_name": "MyModel",
    "model_description": "A sample model",
    "model_version": "1.0.0",
    "model_author": "Your Name"
}
response = client.inference.upload_model(model_data, metadata)
if response.success:
    print(f"Model uploaded successfully. UID: {response.model_uid}")
else:
    print(f"Failed to upload model: {response.error}")
```

#### Example: Run Inference

```python
# Prepare input tensor
input_tensor = {
    "values": [0.1, 0.2, 0.3],
    "shape": [{"size": 3, "name": "input", "dynamic": False}]
}
inputs = {"input_tensor": input_tensor}

# Perform inference
response = client.inference.forward(model_uid="your_model_uid", inputs=inputs)
if not response.get('error'):
    outputs = response['outputs']
    print(f"Inference outputs: {outputs}")
else:
    print(f"Inference failed: {response['error']}")
```

### Simulation Service

Interact with the simulation environment.

#### Example: Reset the Simulation

```python
# Reset simulation with specific parameters
response = client.sim.reset(
    initial_state={"qpos": [0.0, 0.0, 0.0]},
    randomize=True
)
if response.success:
    print("Simulation reset successfully.")
else:
    print(f"Failed to reset simulation: {response.error}")
```

#### Example: Step the Simulation

```python
# Step the simulation forward by 10 steps
response = client.sim.step(num_steps=10)
if response.success:
    print("Simulation stepped forward.")
else:
    print(f"Failed to step simulation: {response.error}")
```

### Closing the Client

When you're done using the client, be sure to close the gRPC channel:

```python
client.close()
```