# sim

Sim service client.

## Classes

### JointPosition (dict)

dict() -> new empty dictionary
dict(mapping) -> new dictionary initialized from a mapping object's
    (key, value) pairs
dict(iterable) -> new dictionary initialized as if via:
    d = {}
    for k, v in iterable:
        d[k] = v
dict(**kwargs) -> new dictionary initialized with the name=value pairs
    in the keyword argument list.  For example:  dict(one=1, two=2)

### ResetRequest (dict)

dict() -> new empty dictionary
dict(mapping) -> new dictionary initialized from a mapping object's
    (key, value) pairs
dict(iterable) -> new dictionary initialized as if via:
    d = {}
    for k, v in iterable:
        d[k] = v
dict(**kwargs) -> new dictionary initialized with the name=value pairs
    in the keyword argument list.  For example:  dict(one=1, two=2)

### SimServiceClient (AsyncClientBase)

Client for the SimulationService.

#### __init__(self, channel: grpc.aio._base_channel.Channel) -> None


#### get_parameters(self) -> kos.sim_pb2.GetParametersResponse

Get current simulation parameters.

**Returns:**
    GetParametersResponse containing current parameters and any error

#### reset(self, **kwargs: Unpack[sim.ResetRequest]) -> kos.common_pb2.ActionResponse

Reset the simulation to its initial state.

**Arguments:**
- ***kwargs*: Reset parameters that may include:
- *initial_state*: DefaultPosition to reset to
- *randomize*: Whether to randomize the initial state

Example:
```python
>>> client.reset(
...     initial_state={"qpos": [0.0, 0.0, 0.0]},
...     randomize=True
... )

```
**Returns:**
    ActionResponse indicating success/failure

#### set_parameters(self, **kwargs: Unpack[sim.SimulationParameters]) -> kos.common_pb2.ActionResponse

Set simulation parameters.

Example:
```python
```
>>> client.set_parameters(
...     time_scale=1.0,
...     gravity=9.81,
... )

**Arguments:**
- ***kwargs*: Parameters that may include:
- *time_scale*: Simulation time scale
- *gravity*: Gravity constant
- *initial_state*: Default position state

**Returns:**
    ActionResponse indicating success/failure

#### set_paused(self, paused: bool) -> kos.common_pb2.ActionResponse

Pause or unpause the simulation.

**Arguments:**
- *paused*: True to pause, False to unpause

**Returns:**
    ActionResponse indicating success/failure

#### step(self, num_steps: int, step_size: float | None = None) -> kos.common_pb2.ActionResponse

Step the simulation forward.

**Arguments:**
- *num_steps*: Number of simulation steps to take
- *step_size*: Optional time per step in seconds

**Returns:**
    ActionResponse indicating success/failure

### SimulationParameters (dict)

dict() -> new empty dictionary
dict(mapping) -> new dictionary initialized from a mapping object's
    (key, value) pairs
dict(iterable) -> new dictionary initialized as if via:
    d = {}
    for k, v in iterable:
        d[k] = v
dict(**kwargs) -> new dictionary initialized with the name=value pairs
    in the keyword argument list.  For example:  dict(one=1, two=2)

### StartingPosition (dict)

dict() -> new empty dictionary
dict(mapping) -> new dictionary initialized from a mapping object's
    (key, value) pairs
dict(iterable) -> new dictionary initialized as if via:
    d = {}
    for k, v in iterable:
        d[k] = v
dict(**kwargs) -> new dictionary initialized with the name=value pairs
    in the keyword argument list.  For example:  dict(one=1, two=2)

### StartingQuaternion (dict)

dict() -> new empty dictionary
dict(mapping) -> new dictionary initialized from a mapping object's
    (key, value) pairs
dict(iterable) -> new dictionary initialized as if via:
    d = {}
    for k, v in iterable:
        d[k] = v
dict(**kwargs) -> new dictionary initialized with the name=value pairs
    in the keyword argument list.  For example:  dict(one=1, two=2)

### StepRequest (dict)

dict() -> new empty dictionary
dict(mapping) -> new dictionary initialized from a mapping object's
    (key, value) pairs
dict(iterable) -> new dictionary initialized as if via:
    d = {}
    for k, v in iterable:
        d[k] = v
dict(**kwargs) -> new dictionary initialized with the name=value pairs
    in the keyword argument list.  For example:  dict(one=1, two=2)
