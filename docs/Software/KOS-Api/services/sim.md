# sim

Sim service client.

## Classes

### JointPosition (T, y, p, e, d, D, i, c, t)


### ResetRequest (T, y, p, e, d, D, i, c, t)


### SimServiceClient (A, s, y, n, c, C, l, i, e, n, t, B, a, s, e)

Client for the SimulationService.

#### __init__self, channel: grpc.aio.Channel


#### get_parametersself

Get current simulation parameters.

**Returns:**
            GetParametersResponse containing current parameters and any error

#### resetself, **kwargs: Unpack[ResetRequest]

Reset the simulation to its initial state.

**Arguments:**
- ***kwargs*: Reset parameters that may include:
- *initial_state*: DefaultPosition to reset to
- *randomize*: Whether to randomize the initial state

- *Example*: 
```python
            >>> client.reset(
- *...     initial_state={"qpos"*: [0.0, 0.0, 0.0]},
            ...     randomize=True
            ... )

```
**Returns:**
            ActionResponse indicating success/failure

#### set_parametersself, **kwargs: Unpack[SimulationParameters]

Set simulation parameters.

        Example:
```python
        >>> client.set_parameters(
        ...     time_scale=1.0,
        ...     gravity=9.81,
        ... )

```
**Arguments:**
- ***kwargs*: Parameters that may include:
- *time_scale*: Simulation time scale
- *gravity*: Gravity constant
- *initial_state*: Default position state

**Returns:**
            ActionResponse indicating success/failure

#### set_pausedself, paused: bool

Pause or unpause the simulation.

**Arguments:**
- *paused*: True to pause, False to unpause

**Returns:**
            ActionResponse indicating success/failure

#### stepself, num_steps: int, step_size: float | None = None

Step the simulation forward.

**Arguments:**
- *num_steps*: Number of simulation steps to take
- *step_size*: Optional time per step in seconds

**Returns:**
            ActionResponse indicating success/failure

### SimulationParameters (T, y, p, e, d, D, i, c, t)


### StartingPosition (T, y, p, e, d, D, i, c, t)


### StartingQuaternion (T, y, p, e, d, D, i, c, t)


### StepRequest (T, y, p, e, d, D, i, c, t)

