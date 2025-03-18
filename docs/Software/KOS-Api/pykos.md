<a id="client"></a>

# client

KOS client.

<a id="client.KOS"></a>

## KOS Objects

```python
class KOS()
```

KOS client.

Args:
    ip (str, optional): IP address of the robot running KOS. Defaults to localhost.
    port (int, optional): Port of the robot running KOS. Defaults to 50051.

Attributes:
    imu (IMUServiceClient): Client for the IMU service.

<a id="client.KOS.connect"></a>

#### connect

```python
def connect() -> None
```

Connect to the gRPC server and initialize service clients.

<a id="client.KOS.close"></a>

#### close

```python
async def close() -> None
```

Close the gRPC channel.

<a id="__init__"></a>

# \_\_init\_\_

KOS Python client.

<a id="services"></a>

# services

KOS service clients.

<a id="services.add_sync_version"></a>

#### add\_sync\_version

```python
def add_sync_version(
        async_func: Callable[..., Coroutine[Any, Any, T]]) -> Callable[..., T]
```

Create a synchronous version of an async function.

<a id="services.AsyncClientBase"></a>

## AsyncClientBase Objects

```python
class AsyncClientBase(ABC)
```

Base class for async gRPC clients that automatically adds sync versions of async methods.

<a id="services.sound"></a>

# services.sound

Sound service client.

<a id="services.sound.AudioCapability"></a>

## AudioCapability Objects

```python
class AudioCapability(TypedDict)
```

Information about audio capabilities.

Args:
    sample_rates: List of supported sample rates (e.g., 44100, 48000)
    bit_depths: List of supported bit depths (e.g., 16, 24, 32)
    channels: List of supported channel counts (e.g., 1, 2)
    available: Whether this capability is available

<a id="services.sound.AudioInfo"></a>

## AudioInfo Objects

```python
class AudioInfo(TypedDict)
```

Information about audio system capabilities.

Args:
    playback: Playback capabilities
    recording: Recording capabilities
    error: Optional error information

<a id="services.sound.AudioConfig"></a>

## AudioConfig Objects

```python
class AudioConfig(TypedDict)
```

Audio configuration parameters.

Args:
    sample_rate: Sample rate in Hz (e.g., 44100)
    bit_depth: Bit depth (e.g., 16)
    channels: Number of channels (1 for mono, 2 for stereo)

<a id="services.sound.SoundServiceClient"></a>

## SoundServiceClient Objects

```python
class SoundServiceClient(AsyncClientBase)
```

Client for the SoundService.

This service allows playing audio through speakers and recording from microphones.

<a id="services.sound.SoundServiceClient.__init__"></a>

#### \_\_init\_\_

```python
def __init__(channel: grpc.aio.Channel) -> None
```

Initialize the sound service client.

Args:
    channel: gRPC channel to use for communication.

<a id="services.sound.SoundServiceClient.get_audio_info"></a>

#### get\_audio\_info

```python
async def get_audio_info() -> AudioInfo
```

Get information about audio capabilities.

Returns:
    AudioInfo containing playback and recording capabilities.

<a id="services.sound.SoundServiceClient.play_audio"></a>

#### play\_audio

```python
async def play_audio(
        audio_iterator: AsyncIterator[bytes],
        **kwargs: Unpack[AudioConfig]) -> common_pb2.ActionResponse
```

Stream PCM audio data to the speaker.

Args:
    audio_iterator: Iterator yielding chunks of PCM audio data
    **kwargs: Audio configuration parameters
        sample_rate: Sample rate in Hz (e.g., 44100)
        bit_depth: Bit depth (e.g., 16)
        channels: Number of channels (1 for mono, 2 for stereo)

Returns:
    ActionResponse indicating success/failure of the playback operation.

Example:
    >>> config = AudioConfig(sample_rate=44100, bit_depth=16, channels=2)
    >>> with open('audio.raw', 'rb') as f:
    ...     def chunks():
    ...         while chunk := f.read(4096):
    ...             yield chunk
    ...     response = client.play_audio(chunks(), config)

<a id="services.sound.SoundServiceClient.record_audio"></a>

#### record\_audio

```python
async def record_audio(
        duration_ms: int = 0,
        **kwargs: Unpack[AudioConfig]) -> AsyncGenerator[bytes, None]
```

Record PCM audio data from the microphone.

Args:
    duration_ms: Recording duration in milliseconds (0 for continuous)
    **kwargs: Audio configuration parameters
        sample_rate: Sample rate in Hz (e.g., 44100)
        bit_depth: Bit depth (e.g., 16)
        channels: Number of channels (1 for mono, 2 for stereo)

Yields:
    Chunks of PCM audio data.

Example:
    >>> config = AudioConfig(sample_rate=44100, bit_depth=16, channels=1)
    >>> with open('recording.raw', 'wb') as f:
    ...     for chunk in client.record_audio(duration_ms=5000, **config):
    ...         f.write(chunk)

<a id="services.sound.SoundServiceClient.stop_recording"></a>

#### stop\_recording

```python
async def stop_recording() -> common_pb2.ActionResponse
```

Stop an ongoing recording session.

Returns:
    ActionResponse indicating success/failure of the stop operation.

<a id="services.sim"></a>

# services.sim

Sim service client.

<a id="services.sim.SimServiceClient"></a>

## SimServiceClient Objects

```python
class SimServiceClient(AsyncClientBase)
```

Client for the SimulationService.

<a id="services.sim.SimServiceClient.reset"></a>

#### reset

```python
async def reset(**kwargs: Unpack[ResetRequest]) -> common_pb2.ActionResponse
```

Reset the simulation to its initial state.

Args:
    **kwargs: Reset parameters that may include:
             initial_state: DefaultPosition to reset to
             randomize: Whether to randomize the initial state

Example:
    >>> client.reset(
    ...     initial_state={"qpos": [0.0, 0.0, 0.0]},
    ...     randomize=True
    ... )

Returns:
    ActionResponse indicating success/failure

<a id="services.sim.SimServiceClient.set_paused"></a>

#### set\_paused

```python
async def set_paused(paused: bool) -> common_pb2.ActionResponse
```

Pause or unpause the simulation.

Args:
    paused: True to pause, False to unpause

Returns:
    ActionResponse indicating success/failure

<a id="services.sim.SimServiceClient.step"></a>

#### step

```python
async def step(num_steps: int,
               step_size: float | None = None) -> common_pb2.ActionResponse
```

Step the simulation forward.

Args:
    num_steps: Number of simulation steps to take
    step_size: Optional time per step in seconds

Returns:
    ActionResponse indicating success/failure

<a id="services.sim.SimServiceClient.set_parameters"></a>

#### set\_parameters

```python
async def set_parameters(**kwargs: Unpack[SimulationParameters]
                         ) -> common_pb2.ActionResponse
```

Set simulation parameters.

Example:
>>> client.set_parameters(
...     time_scale=1.0,
...     gravity=9.81,
... )

Args:
    **kwargs: Parameters that may include:
             time_scale: Simulation time scale
             gravity: Gravity constant
             initial_state: Default position state

Returns:
    ActionResponse indicating success/failure

<a id="services.sim.SimServiceClient.get_parameters"></a>

#### get\_parameters

```python
async def get_parameters() -> sim_pb2.GetParametersResponse
```

Get current simulation parameters.

Returns:
    GetParametersResponse containing current parameters and any error

<a id="services.process_manager"></a>

# services.process\_manager

Process manager service client.

<a id="services.process_manager.ProcessManagerServiceClient"></a>

## ProcessManagerServiceClient Objects

```python
class ProcessManagerServiceClient(AsyncClientBase)
```

Client for the ProcessManagerService.

<a id="services.process_manager.ProcessManagerServiceClient.start_kclip"></a>

#### start\_kclip

```python
async def start_kclip(action: str) -> process_manager_pb2.KClipStartResponse
```

Start KClip recording.

Args:
    action: The action string for the KClip request

Returns:
    The response from the server.

<a id="services.process_manager.ProcessManagerServiceClient.stop_kclip"></a>

#### stop\_kclip

```python
async def stop_kclip(request: Empty = Empty()
                     ) -> process_manager_pb2.KClipStopResponse
```

Stop KClip recording.

Returns:
    The response from the server.

<a id="services.inference"></a>

# services.inference

Inference service client.

<a id="services.inference.ModelMetadata"></a>

## ModelMetadata Objects

```python
class ModelMetadata(TypedDict)
```

Model metadata for uploading models.

All fields are optional and can be used to provide additional information about the model.

<a id="services.inference.TensorDimension"></a>

## TensorDimension Objects

```python
class TensorDimension(TypedDict)
```

Information about a tensor dimension.

Args:
    size: Size of this dimension
    name: Name of this dimension (e.g., "batch", "channels", "height")
    dynamic: Whether this dimension can vary (e.g., batch size)

<a id="services.inference.Tensor"></a>

## Tensor Objects

```python
class Tensor(TypedDict)
```

A tensor containing data.

Args:
    values: Tensor values in row-major order
    shape: List of dimension information

<a id="services.inference.ForwardResponse"></a>

## ForwardResponse Objects

```python
class ForwardResponse(TypedDict)
```

Response from running model inference.

Args:
    outputs: Dictionary mapping tensor names to output tensors
    error: Optional error information if inference failed

<a id="services.inference.ModelInfo"></a>

## ModelInfo Objects

```python
class ModelInfo(TypedDict)
```

Information about a model.

Args:
    uid: Model UID (assigned by server)
    metadata: Model metadata
    input_specs: Expected input tensor specifications
    output_specs: Expected output tensor specifications
    description: str

<a id="services.inference.GetModelsInfoResponse"></a>

## GetModelsInfoResponse Objects

```python
class GetModelsInfoResponse(TypedDict)
```

Response containing information about available models.

<a id="services.inference.InferenceServiceClient"></a>

## InferenceServiceClient Objects

```python
class InferenceServiceClient(AsyncClientBase)
```

Client for the InferenceService.

This service allows uploading models and running inference on them.

<a id="services.inference.InferenceServiceClient.__init__"></a>

#### \_\_init\_\_

```python
def __init__(channel: grpc.aio.Channel) -> None
```

Initialize the inference service client.

Args:
    channel: gRPC channel to use for communication.

<a id="services.inference.InferenceServiceClient.upload_model"></a>

#### upload\_model

```python
async def upload_model(
    model_data: bytes,
    metadata: ModelMetadata | None = None
) -> inference_pb2.UploadModelResponse
```

Upload a model to the robot.

Example:
>>> client.upload_model(model_data,
... metadata={"model_name": "MyModel",
... "model_description": "A model for inference",
... "model_version": "1.0.0",
... "model_author": "John Doe"})

Args:
    model_data: The binary model data to upload.
    metadata: Optional metadata about the model that can include:
             model_name: Name of the model
             model_description: Description of the model
             model_version: Version of the model
             model_author: Author of the model

Returns:
    UploadModelResponse containing the model UID and any error information.

<a id="services.inference.InferenceServiceClient.load_models"></a>

#### load\_models

```python
async def load_models(uids: list[str]) -> inference_pb2.LoadModelsResponse
```

Load models from the robot's filesystem.

Args:
    uids: List of model UIDs to load.

Returns:
    LoadModelsResponse containing information about the loaded models.

<a id="services.inference.InferenceServiceClient.unload_models"></a>

#### unload\_models

```python
async def unload_models(uids: list[str]) -> common_pb2.ActionResponse
```

Unload models from the robot's filesystem.

Args:
    uids: List of model UIDs to unload.

Returns:
    ActionResponse indicating success/failure of the unload operation.

<a id="services.inference.InferenceServiceClient.get_models_info"></a>

#### get\_models\_info

```python
async def get_models_info(
        model_uids: list[str] | None = None) -> GetModelsInfoResponse
```

Get information about available models.

Args:
    model_uids: Optional list of specific model UIDs to get info for.
               If None, returns info for all models.

Returns:
    GetModelsInfoResponse containing:
        models: List of ModelInfo objects
        error: Optional error information if fetching failed

<a id="services.inference.InferenceServiceClient.forward"></a>

#### forward

```python
async def forward(model_uid: str, inputs: dict[str,
                                               Tensor]) -> ForwardResponse
```

Run inference using a specified model.

Args:
    model_uid: The UID of the model to use for inference.
    inputs: Dictionary mapping tensor names to tensors.

Returns:
    ForwardResponse containing:
        outputs: Dictionary mapping tensor names to output tensors
        error: Optional error information if inference failed

<a id="services.imu"></a>

# services.imu

IMU service client.

<a id="services.imu.IMUServiceClient"></a>

## IMUServiceClient Objects

```python
class IMUServiceClient(AsyncClientBase)
```

Client for the IMUService.

<a id="services.imu.IMUServiceClient.get_imu_values"></a>

#### get\_imu\_values

```python
async def get_imu_values() -> imu_pb2.IMUValuesResponse
```

Get the latest IMU sensor values.

Returns:
    ImuValuesResponse: The latest IMU sensor values.

<a id="services.imu.IMUServiceClient.get_imu_advanced_values"></a>

#### get\_imu\_advanced\_values

```python
async def get_imu_advanced_values() -> imu_pb2.IMUAdvancedValuesResponse
```

Get the latest IMU advanced values.

Returns:
    ImuAdvancedValuesResponse: The latest IMU advanced values.

<a id="services.imu.IMUServiceClient.get_euler_angles"></a>

#### get\_euler\_angles

```python
async def get_euler_angles() -> imu_pb2.EulerAnglesResponse
```

Get the latest Euler angles.

Returns:
    EulerAnglesResponse: The latest Euler angles.

<a id="services.imu.IMUServiceClient.get_quaternion"></a>

#### get\_quaternion

```python
async def get_quaternion() -> imu_pb2.QuaternionResponse
```

Get the latest quaternion.

Returns:
    QuaternionResponse: The latest quaternion.

<a id="services.imu.IMUServiceClient.zero"></a>

#### zero

```python
async def zero(duration: float = 1.0,
               **kwargs: Unpack[ZeroIMURequest]) -> common_pb2.ActionResponse
```

Zero the IMU.

Example:
    >>> await zero(duration=1.0,
    ...     max_retries=3,
    ...     max_angular_error=1.0,
    ...     max_velocity=1.0,
    ...     max_acceleration=1.0
    ... )

Args:
    duration: Duration in seconds for zeroing operation
    **kwargs: Additional zeroing parameters that may include:
             max_retries: Maximum number of retries
             max_angular_error: Maximum angular error during zeroing
             max_velocity: Maximum velocity during zeroing
             max_acceleration: Maximum acceleration during zeroing

Returns:
    ActionResponse: The response from the zero operation.

<a id="services.imu.IMUServiceClient.calibrate"></a>

#### calibrate

```python
async def calibrate() -> imu_pb2.CalibrateIMUResponse
```

Calibrate the IMU.

This starts a long-running calibration operation. The operation can be monitored
using get_calibration_status().

Returns:
    CalibrationMetadata: Metadata about the calibration operation.

<a id="services.led_matrix"></a>

# services.led\_matrix

LED Matrix service client.

<a id="services.led_matrix.MatrixInfo"></a>

## MatrixInfo Objects

```python
class MatrixInfo(TypedDict)
```

Information about the LED matrix.

Args:
    width: Width in pixels
    height: Height in pixels
    brightness_levels: Number of brightness levels supported (1 for binary on/off)
    color_capable: Whether the matrix supports color
    bits_per_pixel: Number of bits used to represent each pixel
    error: Optional error information

<a id="services.led_matrix.ImageData"></a>

## ImageData Objects

```python
class ImageData(TypedDict)
```

Image data to be written to the LED matrix.

Args:
    buffer: Raw image data bytes
    width: Image width in pixels
    height: Image height in pixels
    format: Pixel format specification (e.g. 'RGB888', 'BGR888', 'RGB565', 'MONO8')
    brightness: Global brightness level (0-255)

<a id="services.led_matrix.LEDMatrixServiceClient"></a>

## LEDMatrixServiceClient Objects

```python
class LEDMatrixServiceClient(AsyncClientBase)
```

Client for the LEDMatrixService.

This service allows controlling an LED matrix display.

<a id="services.led_matrix.LEDMatrixServiceClient.__init__"></a>

#### \_\_init\_\_

```python
def __init__(channel: grpc.aio.Channel) -> None
```

Initialize the LED matrix service client.

Args:
    channel: gRPC channel to use for communication.

<a id="services.led_matrix.LEDMatrixServiceClient.get_matrix_info"></a>

#### get\_matrix\_info

```python
async def get_matrix_info() -> MatrixInfo
```

Get information about the LED matrix including dimensions and capabilities.

Returns:
    MatrixInfo containing:
        width: Width in pixels
        height: Height in pixels
        brightness_levels: Number of brightness levels supported
        color_capable: Whether the matrix supports color
        bits_per_pixel: Number of bits used to represent each pixel
        error: Optional error information

<a id="services.led_matrix.LEDMatrixServiceClient.write_buffer"></a>

#### write\_buffer

```python
async def write_buffer(buffer: bytes) -> common_pb2.ActionResponse
```

Write binary on/off states to the LED matrix.

The buffer should be width * height / 8 bytes long, where each bit
represents one LED's on/off state.

Args:
    buffer: Binary buffer containing LED states

Returns:
    ActionResponse indicating success/failure of the write operation.

<a id="services.led_matrix.LEDMatrixServiceClient.write_color_buffer"></a>

#### write\_color\_buffer

```python
async def write_color_buffer(**kwargs: Unpack[ImageData]
                             ) -> common_pb2.ActionResponse
```

Write image data to the LED matrix.

Args:
    **kwargs: Image data containing the raw bytes, dimensions and format
        buffer: Raw image data bytes
        width: Image width in pixels
        height: Image height in pixels
        format: Pixel format specification (e.g. 'RGB888', 'BGR888', 'RGB565', 'MONO8')
        brightness: Global brightness level (0-255)

Returns:
    ActionResponse indicating success/failure of the write operation.

<a id="services.actuator"></a>

# services.actuator

Actuator service client.

<a id="services.actuator.ActuatorServiceClient"></a>

## ActuatorServiceClient Objects

```python
class ActuatorServiceClient(AsyncClientBase)
```

Client for the ActuatorService.

<a id="services.actuator.ActuatorServiceClient.calibrate"></a>

#### calibrate

```python
async def calibrate(actuator_id: int) -> CalibrationMetadata
```

Calibrate an actuator.

<a id="services.actuator.ActuatorServiceClient.get_calibration_status"></a>

#### get\_calibration\_status

```python
async def get_calibration_status(actuator_id: int) -> str | None
```

Get the calibration status of an actuator.

<a id="services.actuator.ActuatorServiceClient.command_actuators"></a>

#### command\_actuators

```python
async def command_actuators(
        commands: list[ActuatorCommand]
) -> actuator_pb2.CommandActuatorsResponse
```

Command multiple actuators at once.

Example:
    >>> command_actuators([
    ...     {"actuator_id": 1, "position": 90.0, "velocity": 100.0, "torque": 1.0},
    ...     {"actuator_id": 2, "position": 180.0},
    ... ])

Args:
    commands: List of dictionaries containing actuator commands.
             Each dict should have 'actuator_id' and optionally 'position',
             'velocity', and 'torque'.

Returns:
    List of ActionResult objects indicating success/failure for each command.

<a id="services.actuator.ActuatorServiceClient.configure_actuator"></a>

#### configure\_actuator

```python
async def configure_actuator(**kwargs: Unpack[ConfigureActuatorRequest]
                             ) -> common_pb2.ActionResult
```

Configure an actuator's parameters.

Example:
    >>> configure_actuator(
    ...     actuator_id=1,
    ...     kp=1.0,
    ...     kd=0.1,
    ...     ki=0.01,
    ...     acceleration=2230,
    ...     max_torque=100.0,
    ...     protective_torque=None,
    ...     protection_time=None,
    ...     torque_enabled=True,
    ...     new_actuator_id=None,
    ...     zero_position=True,
    ... )

    >>> configure_actuator(
    ...     actuator_id=2,
    ...     kp=1.0,
    ...     kd=0.1,
    ...     torque_enabled=True,
    ... )

Args:
    actuator_id: ID of the actuator to configure
    **kwargs: Configuration parameters that may include:
             kp, kd, ki, max_torque, protective_torque,
             protection_time, torque_enabled, new_actuator_id

Returns:
    ActionResponse indicating success/failure

<a id="services.actuator.ActuatorServiceClient.get_actuators_state"></a>

#### get\_actuators\_state

```python
async def get_actuators_state(
    actuator_ids: list[int] | None = None
) -> actuator_pb2.GetActuatorsStateResponse
```

Get the state of multiple actuators.

Example:
    >>> get_actuators_state([1, 2])

Args:
    actuator_ids: List of actuator IDs to query. If None, gets state of all actuators.

Returns:
    List of ActuatorStateResponse objects containing the state information

<a id="services.actuator.ActuatorServiceClient.move_to_position"></a>

#### move\_to\_position

```python
async def move_to_position(positions: list[ActuatorPosition],
                           num_seconds: float,
                           configure_actuators: list[ConfigureActuatorRequest]
                           | None = None,
                           commands_per_second: int = 10,
                           torque_enabled: bool | None = None) -> None
```

Helper function for moving actuators to a target position.

This first reads the current position of the actuators, then moves them
to the target positions at a rate of `commands_per_second` commands per
second.

We can additionally use this command to safely configure the actuator
PD parameters after setting the target position to the current position.

Args:
    positions: The actuator target positions.
    num_seconds: How long to take the actuators to move to the target
        positions.
    configure_actuators: List of dictionaries containing actuator
        configuration parameters.
    commands_per_second: How many commands to send per second.
    torque_enabled: Whether to enable torque for the actuators.

<a id="services.actuator.ActuatorServiceClient.zero_actuators"></a>

#### zero\_actuators

```python
async def zero_actuators(actuator_id: int,
                         zero_position: float,
                         configure_actuator: ConfigureActuatorRequest
                         | None = None,
                         target_velocity: float = 0.25,
                         commands_per_second: int = 10,
                         move_back_seconds: float = 3.0) -> None
```

Helper method for zeroing an actuator.

This function works to zero the actuator against an endstop, by moving
the actuator until it reaches that endstop, then moving it back a small
amount.

We can choose which endstop to zero against by setting the sign of
`zero_position`. If it is positive, then we rotate counterclockwise
until we reach an endstop, then back by this amount. If it is negative,
then we rotate clockwise until we reach an endstop, then back by this
amount.

Args:
    actuator_id: The ID of the actuator to zero.
    zero_position: The position to move the actuator back by after
        reaching the endstop.
    configure_actuator: Configuration parameters to set on the actuator
        before zeroing.
    target_velocity: The velocity to move the actuator at.
    commands_per_second: How many commands to send per second.
    move_back_seconds: How long to move the actuator back by after
        reaching the endstop.

