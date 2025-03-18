# Sound Service

The Sound Service provides audio playback and recording capabilities, with support for multiple audio formats and sample rates.

## Classes

### AudioCapability (TypedDict)

Information about audio hardware capabilities.

#### Fields

- **sample_rates**: list[int] - List of supported sample rates in Hz (e.g., 44100, 48000)
- **bit_depths**: list[int] - List of supported bit depths (e.g., 16, 24, 32)
- **channels**: list[int] - List of supported channel counts (e.g., 1, 2)
- **available**: bool - Whether this capability is available

### AudioInfo (TypedDict)

Information about the audio system's capabilities.

#### Fields

- **playback**: AudioCapability - Playback capabilities
- **recording**: AudioCapability - Recording capabilities
- **error**: NotRequired[Error | None] - Optional error information

### AudioConfig (TypedDict)

Audio configuration parameters.

#### Fields

- **sample_rate**: int - Sample rate in Hz (e.g., 44100)
- **bit_depth**: int - Bit depth (e.g., 16)
- **channels**: int - Number of channels (1 for mono, 2 for stereo)

### SoundServiceClient (AsyncClientBase)

Client for interacting with the Sound Service.

#### Methods

##### `__init__(self, channel: grpc.aio.Channel)`

Initialize the sound service client with a gRPC channel.

##### `get_audio_info(self) -> AudioInfo`

Get information about the audio system's capabilities.

**Returns:**
- AudioInfo containing playback and recording capabilities

**Example:**
```python
info = await sound_client.get_audio_info()
print(f"Playback available: {info.playback.available}")
print(f"Supported sample rates: {info.playback.sample_rates}")
```

##### `play_sound(self, audio_data: bytes, config: AudioConfig) -> ActionResult`

Play audio data through the audio output device.

**Parameters:**
- audio_data: Raw audio data bytes (WAV format without header)
- config: Audio configuration parameters

**Returns:**
- ActionResult indicating success/failure

**Example:**
```python
# Play a 440Hz sine wave for 1 second
import numpy as np

sample_rate = 44100
duration = 1.0  # seconds
frequency = 440  # Hz
t = np.linspace(0, duration, int(sample_rate * duration), False)
sine_wave = np.sin(2 * np.pi * frequency * t)
audio_data = (sine_wave * 32767).astype(np.int16).tobytes()

config = {
    "sample_rate": sample_rate,
    "bit_depth": 16,
    "channels": 1
}

await sound_client.play_sound(audio_data, config)
```

##### `stop_playback(self) -> ActionResult`

Stop any currently playing audio.

**Returns:**
- ActionResult indicating success/failure

**Example:**
```python
await sound_client.stop_playback()
```

##### `play_tone(self, frequency: float, duration_ms: int, volume: float = 1.0) -> ActionResult`

Play a simple sine wave tone at the specified frequency.

**Parameters:**
- frequency: Tone frequency in Hz
- duration_ms: Duration in milliseconds
- volume: Volume level from 0.0 to 1.0

**Returns:**
- ActionResult indicating success/failure

**Example:**
```python
# Play a 1kHz tone for 500ms at 75% volume
await sound_client.play_tone(
    frequency=1000,
    duration_ms=500,
    volume=0.75
)
```

##### `start_recording(self, config: AudioConfig, max_duration_ms: int = 0) -> ActionResult`

Start recording audio from the microphone.

**Parameters:**
- config: Audio configuration parameters
- max_duration_ms: Maximum recording duration in milliseconds (0 for unlimited)

**Returns:**
- ActionResult indicating success/failure

**Example:**
```python
config = {
    "sample_rate": 16000,
    "bit_depth": 16,
    "channels": 1
}

await sound_client.start_recording(
    config=config,
    max_duration_ms=5000  # 5 seconds
)
```

##### `stop_recording(self) -> bytes`

Stop the current recording and retrieve the recorded audio data.

**Returns:**
- Bytes containing the recorded audio data

**Example:**
```python
# Start recording
await sound_client.start_recording({
    "sample_rate": 16000,
    "bit_depth": 16,
    "channels": 1
})

# Wait for a bit
await asyncio.sleep(3)

# Stop and get the recording
audio_data = await sound_client.stop_recording()
print(f"Recorded {len(audio_data)} bytes of audio")
```

##### `play_file(self, file_path: str) -> ActionResult`

Play an audio file from the file system.

**Parameters:**
- file_path: Path to the audio file (supports WAV, MP3, OGG)

**Returns:**
- ActionResult indicating success/failure

**Example:**
```python
await sound_client.play_file("/path/to/music.mp3")
```

##### `set_volume(self, volume: float) -> ActionResult`

Set the global audio output volume.

**Parameters:**
- volume: Volume level from 0.0 (silent) to 1.0 (maximum)

**Returns:**
- ActionResult indicating success/failure

**Example:**
```python
await sound_client.set_volume(0.8)  # 80% volume
```