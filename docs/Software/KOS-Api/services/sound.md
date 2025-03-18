# sound

Sound service client.

## Classes

### AudioCapability (T, y, p, e, d, D, i, c, t)

Information about audio capabilities.

**Arguments:**
- *sample_rates*: List of supported sample rates (e.g., 44100, 48000)
- *bit_depths*: List of supported bit depths (e.g., 16, 24, 32)
- *channels*: List of supported channel counts (e.g., 1, 2)
- *available*: Whether this capability is available

### AudioConfig (T, y, p, e, d, D, i, c, t)

Audio configuration parameters.

**Arguments:**
- *sample_rate*: Sample rate in Hz (e.g., 44100)
- *bit_depth*: Bit depth (e.g., 16)
- *channels*: Number of channels (1 for mono, 2 for stereo)

### AudioInfo (T, y, p, e, d, D, i, c, t)

Information about audio system capabilities.

**Arguments:**
- *playback*: Playback capabilities
- *recording*: Recording capabilities
- *error*: Optional error information

### SoundServiceClient (A, s, y, n, c, C, l, i, e, n, t, B, a, s, e)

Client for the SoundService.

    This service allows playing audio through speakers and recording from microphones.

#### __init__self, channel: grpc.aio.Channel

Initialize the sound service client.

**Arguments:**
- *channel*: gRPC channel to use for communication.

#### get_audio_infoself

Get information about audio capabilities.

**Returns:**
            AudioInfo containing playback and recording capabilities.

#### play_audioself, audio_iterator: AsyncIterator[bytes], **kwargs: Unpack[AudioConfig]

Stream PCM audio data to the speaker.

**Arguments:**
- *audio_iterator*: Iterator yielding chunks of PCM audio data
- ***kwargs*: Audio configuration parameters
- *sample_rate*: Sample rate in Hz (e.g., 44100)
- *bit_depth*: Bit depth (e.g., 16)
- *channels*: Number of channels (1 for mono, 2 for stereo)

**Returns:**
            ActionResponse indicating success/failure of the playback operation.

        Example:
```python
            >>> config = AudioConfig(sample_rate=44100, bit_depth=16, channels=2)
            >>> with open('audio.raw', 'rb') as f:
            ...     def chunks():
            ...         while chunk := f.read(4096):
            ...             yield chunk
            ...     response = client.play_audio(chunks(), config)
```

#### record_audioself, duration_ms: int = 0, **kwargs: Unpack[AudioConfig]

Record PCM audio data from the microphone.

**Arguments:**
- *duration_ms*: Recording duration in milliseconds (0 for continuous)
- ***kwargs*: Audio configuration parameters
- *sample_rate*: Sample rate in Hz (e.g., 44100)
- *bit_depth*: Bit depth (e.g., 16)
- *channels*: Number of channels (1 for mono, 2 for stereo)

- *Yields*: 
            Chunks of PCM audio data.

- *Example*: 
```python
            >>> config = AudioConfig(sample_rate=44100, bit_depth=16, channels=1)
- *>>> with open('recording.raw', 'wb') as f*: 
- *...     for chunk in client.record_audio(duration_ms=5000, **config)*: 
            ...         f.write(chunk)
```

#### stop_recordingself

Stop an ongoing recording session.

**Returns:**
            ActionResponse indicating success/failure of the stop operation.

## Functions

### request_iterator

