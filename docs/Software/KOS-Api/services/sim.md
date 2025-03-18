# Simulation Service

The Simulation Service provides control over a physics simulation environment, allowing for robot movement simulation, physics interactions, and virtual testing of robot behaviors.

## Classes

### StartingPosition (TypedDict)

Position in 3D space.

#### Fields

- **x**: float - X-coordinate in meters
- **y**: float - Y-coordinate in meters
- **z**: float - Z-coordinate in meters

### StartingQuaternion (TypedDict)

Orientation in 3D space using quaternion representation.

#### Fields

- **x**: float - X component of quaternion
- **y**: float - Y component of quaternion
- **z**: float - Z component of quaternion
- **w**: float - W component of quaternion (scalar part)

### JointPosition (TypedDict)

Joint configuration.

#### Fields

- **name**: str - Name of the joint
- **pos**: NotRequired[float] - Position/angle of the joint in radians
- **vel**: NotRequired[float] - Velocity of the joint in radians/second

### ResetRequest (TypedDict)

Request to reset the simulation to a particular state.

#### Fields

- **pos**: NotRequired[StartingPosition] - Starting position of the robot
- **quat**: NotRequired[StartingQuaternion] - Starting orientation of the robot
- **joints**: NotRequired[list[JointPosition]] - Starting positions of robot joints

### StepRequest (TypedDict)

Request to step the simulation forward.

#### Fields

- **num_steps**: int - Number of physics steps to simulate
- **step_size**: NotRequired[float] - Duration of each step in seconds

### SimulationParameters (TypedDict)

Parameters controlling the simulation environment.

#### Fields

- **time_scale**: NotRequired[float] - Simulation time scale (1.0 = real-time)
- **gravity**: NotRequired[float] - Gravity strength in m/s²

### SimServiceClient (AsyncClientBase)

Client for interacting with the Simulation Service.

#### Methods

##### `__init__(self, channel: grpc.aio.Channel)`

Initialize the simulation service client with a gRPC channel.

##### `reset(self, **kwargs: Unpack[ResetRequest]) -> ActionResult`

Reset the simulation to a defined state.

**Parameters:**
- **kwargs: Reset parameters (see ResetRequest fields)

**Returns:**
- ActionResult indicating success/failure

**Example:**
```python
result = await sim_client.reset(
    pos={"x": 0.0, "y": 0.0, "z": 0.5},
    quat={"x": 0.0, "y": 0.0, "z": 0.0, "w": 1.0},
    joints=[
        {"name": "left_knee", "pos": 0.5, "vel": 0.0},
        {"name": "right_knee", "pos": 0.5, "vel": 0.0}
    ]
)
```

##### `step(self, num_steps: int, step_size: float = None) -> ActionResult`

Step the simulation forward by a specified number of steps.

**Parameters:**
- num_steps: Number of simulation steps to execute
- step_size: Optional duration of each step in seconds

**Returns:**
- ActionResult indicating success/failure

**Example:**
```python
# Step forward 100 physics steps with default step size
result = await sim_client.step(num_steps=100)

# Step forward 10 physics steps with custom step size
result = await sim_client.step(num_steps=10, step_size=0.002)  # 2ms steps
```

##### `get_state(self) -> SimulationState`

Get the current state of the simulation.

**Returns:**
- SimulationState containing current positions, velocities, etc.

**Example:**
```python
state = await sim_client.get_state()
print(f"Robot position: ({state.position.x}, {state.position.y}, {state.position.z})")
print(f"Simulation time: {state.sim_time}s")
```

##### `set_parameters(self, **kwargs: Unpack[SimulationParameters]) -> ActionResult`

Set simulation parameters.

**Parameters:**
- **kwargs: Simulation parameters (see SimulationParameters fields)

**Returns:**
- ActionResult indicating success/failure

**Example:**
```python
# Set simulation to run at 2x speed with reduced gravity
result = await sim_client.set_parameters(
    time_scale=2.0,
    gravity=5.0  # Mars-like gravity
)
```

##### `get_parameters(self) -> SimulationParameters`

Get current simulation parameters.

**Returns:**
- SimulationParameters containing current settings

**Example:**
```python
params = await sim_client.get_parameters()
print(f"Time scale: {params.time_scale}x")
print(f"Gravity: {params.gravity} m/s²")
```

##### `apply_force(self, body_name: str, force: StartingPosition, position: StartingPosition = None) -> ActionResult`

Apply a force to a body in the simulation.

**Parameters:**
- body_name: Name of the body to apply force to
- force: Force vector in Newtons
- position: Optional position to apply the force (default is center of mass)

**Returns:**
- ActionResult indicating success/failure

**Example:**
```python
# Apply a 10N upward force to the robot's torso
result = await sim_client.apply_force(
    body_name="torso",
    force={"x": 0.0, "y": 0.0, "z": 10.0}
)
```

##### `set_joint_target(self, joint_name: str, position: float, max_force: float = None) -> ActionResult`

Set a target position for a joint.

**Parameters:**
- joint_name: Name of the joint
- position: Target position in radians
- max_force: Maximum force to apply (in N or N·m)

**Returns:**
- ActionResult indicating success/failure

**Example:**
```python
# Set the head joint to look upward
result = await sim_client.set_joint_target(
    joint_name="head_joint",
    position=0.5,  # radians
    max_force=2.0  # Newton-meters
)
```

##### `pause(self) -> ActionResult`

Pause the simulation.

**Returns:**
- ActionResult indicating success/failure

**Example:**
```python
await sim_client.pause()
```

##### `resume(self) -> ActionResult`

Resume the simulation after pausing.

**Returns:**
- ActionResult indicating success/failure

**Example:**
```python
await sim_client.resume()
```