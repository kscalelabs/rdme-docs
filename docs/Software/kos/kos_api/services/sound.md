---
title: sound
---

# sound

#### Help on module sound


NAME
    sound - Sound service client.

CLASSES
    builtins.dict(builtins.object)
        AudioCapability
        AudioConfig
        AudioInfo
    pykos.services.AsyncClientBase(abc.ABC)
        SoundServiceClient

    class AudioCapability(builtins.dict)
     |  Information about audio capabilities.
     |
     |  Args:
     |      sample_rates: List of supported sample rates (e.g., 44100, 48000)
     |      bit_depths: List of supported bit depths (e.g., 16, 24, 32)
     |      channels: List of supported channel counts (e.g., 1, 2)
     |      available: Whether this capability is available
     |
     |  Method resolution order:
     |      AudioCapability
     |      builtins.dict
     |      builtins.object
     |
     |  Data descriptors defined here:
     |
     |  __dict__
     |      dictionary for instance variables
     |
     |  __weakref__
     |      list of weak references to the object
     |
     |  ----------------------------------------------------------------------
     |  Data and other attributes defined here:
     |
     |  __annotations__ = {'available': <class 'bool'>, 'bit_depths': list[int...
     |
     |  __optional_keys__ = frozenset()
     |
     |  __orig_bases__ = (<function TypedDict>,)
     |
     |  __required_keys__ = frozenset({'available', 'bit_depths', 'channels', ...
     |
     |  __total__ = True
     |
     |  ----------------------------------------------------------------------
     |  Methods inherited from builtins.dict:
     |
     |  __contains__(self, key, /)
     |      True if the dictionary has the specified key, else False.
     |
     |  __delitem__(self, key, /)
     |      Delete self[key].
     |
     |  __eq__(self, value, /)
     |      Return self==value.
     |
     |  __ge__(self, value, /)
     |      Return self>=value.
     |
     |  __getattribute__(self, name, /)
     |      Return getattr(self, name).
     |
     |  __getitem__(self, key, /)
     |      Return self[key].
     |
     |  __gt__(self, value, /)
     |      Return self>value.
     |
     |  __init__(self, /, *args, **kwargs)
     |      Initialize self.  See help(type(self)) for accurate signature.
     |
     |  __ior__(self, value, /)
     |      Return self|=value.
     |
     |  __iter__(self, /)
     |      Implement iter(self).
     |
     |  __le__(self, value, /)
     |      Return self<=value.
     |
     |  __len__(self, /)
     |      Return len(self).
     |
     |  __lt__(self, value, /)
     |      Return self<value.
     |
     |  __ne__(self, value, /)
     |      Return self!=value.
     |
     |  __or__(self, value, /)
     |      Return self|value.
     |
     |  __repr__(self, /)
     |      Return repr(self).
     |
     |  __reversed__(self, /)
     |      Return a reverse iterator over the dict keys.
     |
     |  __ror__(self, value, /)
     |      Return value|self.
     |
     |  __setitem__(self, key, value, /)
     |      Set self[key] to value.
     |
     |  __sizeof__(...)
     |      D.__sizeof__() -> size of D in memory, in bytes
     |
     |  clear(...)
     |      D.clear() -> None.  Remove all items from D.
     |
     |  copy(...)
     |      D.copy() -> a shallow copy of D
     |
     |  get(self, key, default=None, /)
     |      Return the value for key if key is in the dictionary, else default.
     |
     |  items(...)
     |      D.items() -> a set-like object providing a view on D's items
     |
     |  keys(...)
     |      D.keys() -> a set-like object providing a view on D's keys
     |
     |  pop(...)
     |      D.pop(k[,d]) -> v, remove specified key and return the corresponding value.
     |
     |      If the key is not found, return the default if given; otherwise,
     |      raise a KeyError.
     |
     |  popitem(self, /)
     |      Remove and return a (key, value) pair as a 2-tuple.
     |
     |      Pairs are returned in LIFO (last-in, first-out) order.
     |      Raises KeyError if the dict is empty.
     |
     |  setdefault(self, key, default=None, /)
     |      Insert key with a value of default if key is not in the dictionary.
     |
     |      Return the value for key if key is in the dictionary, else default.
     |
     |  update(...)
     |      D.update([E, ]**F) -> None.  Update D from dict/iterable E and F.
     |      If E is present and has a .keys() method, then does:  for k in E: D[k] = E[k]
     |      If E is present and lacks a .keys() method, then does:  for k, v in E: D[k] = v
     |      In either case, this is followed by: for k in F:  D[k] = F[k]
     |
     |  values(...)
     |      D.values() -> an object providing a view on D's values
     |
     |  ----------------------------------------------------------------------
     |  Class methods inherited from builtins.dict:
     |
     |  __class_getitem__(...) from typing._TypedDictMeta
     |      See PEP 585
     |
     |  fromkeys(iterable, value=None, /) from typing._TypedDictMeta
     |      Create a new dictionary with keys from iterable and values set to value.
     |
     |  ----------------------------------------------------------------------
     |  Static methods inherited from builtins.dict:
     |
     |  __new__(*args, **kwargs) from builtins.type
     |      Create and return a new object.  See help(type) for accurate signature.
     |
     |  ----------------------------------------------------------------------
     |  Data and other attributes inherited from builtins.dict:
     |
     |  __hash__ = None

    class AudioConfig(builtins.dict)
     |  Audio configuration parameters.
     |
     |  Args:
     |      sample_rate: Sample rate in Hz (e.g., 44100)
     |      bit_depth: Bit depth (e.g., 16)
     |      channels: Number of channels (1 for mono, 2 for stereo)
     |
     |  Method resolution order:
     |      AudioConfig
     |      builtins.dict
     |      builtins.object
     |
     |  Data descriptors defined here:
     |
     |  __dict__
     |      dictionary for instance variables
     |
     |  __weakref__
     |      list of weak references to the object
     |
     |  ----------------------------------------------------------------------
     |  Data and other attributes defined here:
     |
     |  __annotations__ = {'bit_depth': <class 'int'>, 'channels': <class 'int...
     |
     |  __optional_keys__ = frozenset()
     |
     |  __orig_bases__ = (<function TypedDict>,)
     |
     |  __required_keys__ = frozenset({'bit_depth', 'channels', 'sample_rate'}...
     |
     |  __total__ = True
     |
     |  ----------------------------------------------------------------------
     |  Methods inherited from builtins.dict:
     |
     |  __contains__(self, key, /)
     |      True if the dictionary has the specified key, else False.
     |
     |  __delitem__(self, key, /)
     |      Delete self[key].
     |
     |  __eq__(self, value, /)
     |      Return self==value.
     |
     |  __ge__(self, value, /)
     |      Return self>=value.
     |
     |  __getattribute__(self, name, /)
     |      Return getattr(self, name).
     |
     |  __getitem__(self, key, /)
     |      Return self[key].
     |
     |  __gt__(self, value, /)
     |      Return self>value.
     |
     |  __init__(self, /, *args, **kwargs)
     |      Initialize self.  See help(type(self)) for accurate signature.
     |
     |  __ior__(self, value, /)
     |      Return self|=value.
     |
     |  __iter__(self, /)
     |      Implement iter(self).
     |
     |  __le__(self, value, /)
     |      Return self<=value.
     |
     |  __len__(self, /)
     |      Return len(self).
     |
     |  __lt__(self, value, /)
     |      Return self<value.
     |
     |  __ne__(self, value, /)
     |      Return self!=value.
     |
     |  __or__(self, value, /)
     |      Return self|value.
     |
     |  __repr__(self, /)
     |      Return repr(self).
     |
     |  __reversed__(self, /)
     |      Return a reverse iterator over the dict keys.
     |
     |  __ror__(self, value, /)
     |      Return value|self.
     |
     |  __setitem__(self, key, value, /)
     |      Set self[key] to value.
     |
     |  __sizeof__(...)
     |      D.__sizeof__() -> size of D in memory, in bytes
     |
     |  clear(...)
     |      D.clear() -> None.  Remove all items from D.
     |
     |  copy(...)
     |      D.copy() -> a shallow copy of D
     |
     |  get(self, key, default=None, /)
     |      Return the value for key if key is in the dictionary, else default.
     |
     |  items(...)
     |      D.items() -> a set-like object providing a view on D's items
     |
     |  keys(...)
     |      D.keys() -> a set-like object providing a view on D's keys
     |
     |  pop(...)
     |      D.pop(k[,d]) -> v, remove specified key and return the corresponding value.
     |
     |      If the key is not found, return the default if given; otherwise,
     |      raise a KeyError.
     |
     |  popitem(self, /)
     |      Remove and return a (key, value) pair as a 2-tuple.
     |
     |      Pairs are returned in LIFO (last-in, first-out) order.
     |      Raises KeyError if the dict is empty.
     |
     |  setdefault(self, key, default=None, /)
     |      Insert key with a value of default if key is not in the dictionary.
     |
     |      Return the value for key if key is in the dictionary, else default.
     |
     |  update(...)
     |      D.update([E, ]**F) -> None.  Update D from dict/iterable E and F.
     |      If E is present and has a .keys() method, then does:  for k in E: D[k] = E[k]
     |      If E is present and lacks a .keys() method, then does:  for k, v in E: D[k] = v
     |      In either case, this is followed by: for k in F:  D[k] = F[k]
     |
     |  values(...)
     |      D.values() -> an object providing a view on D's values
     |
     |  ----------------------------------------------------------------------
     |  Class methods inherited from builtins.dict:
     |
     |  __class_getitem__(...) from typing._TypedDictMeta
     |      See PEP 585
     |
     |  fromkeys(iterable, value=None, /) from typing._TypedDictMeta
     |      Create a new dictionary with keys from iterable and values set to value.
     |
     |  ----------------------------------------------------------------------
     |  Static methods inherited from builtins.dict:
     |
     |  __new__(*args, **kwargs) from builtins.type
     |      Create and return a new object.  See help(type) for accurate signature.
     |
     |  ----------------------------------------------------------------------
     |  Data and other attributes inherited from builtins.dict:
     |
     |  __hash__ = None

    class AudioInfo(builtins.dict)
     |  Information about audio system capabilities.
     |
     |  Args:
     |      playback: Playback capabilities
     |      recording: Recording capabilities
     |      error: Optional error information
     |
     |  Method resolution order:
     |      AudioInfo
     |      builtins.dict
     |      builtins.object
     |
     |  Data descriptors defined here:
     |
     |  __dict__
     |      dictionary for instance variables
     |
     |  __weakref__
     |      list of weak references to the object
     |
     |  ----------------------------------------------------------------------
     |  Data and other attributes defined here:
     |
     |  __annotations__ = {'error': typing.NotRequired[kos.common_pb2.Error | ...
     |
     |  __optional_keys__ = frozenset({'error'})
     |
     |  __orig_bases__ = (<function TypedDict>,)
     |
     |  __required_keys__ = frozenset({'playback', 'recording'})
     |
     |  __total__ = True
     |
     |  ----------------------------------------------------------------------
     |  Methods inherited from builtins.dict:
     |
     |  __contains__(self, key, /)
     |      True if the dictionary has the specified key, else False.
     |
     |  __delitem__(self, key, /)
     |      Delete self[key].
     |
     |  __eq__(self, value, /)
     |      Return self==value.
     |
     |  __ge__(self, value, /)
     |      Return self>=value.
     |
     |  __getattribute__(self, name, /)
     |      Return getattr(self, name).
     |
     |  __getitem__(self, key, /)
     |      Return self[key].
     |
     |  __gt__(self, value, /)
     |      Return self>value.
     |
     |  __init__(self, /, *args, **kwargs)
     |      Initialize self.  See help(type(self)) for accurate signature.
     |
     |  __ior__(self, value, /)
     |      Return self|=value.
     |
     |  __iter__(self, /)
     |      Implement iter(self).
     |
     |  __le__(self, value, /)
     |      Return self<=value.
     |
     |  __len__(self, /)
     |      Return len(self).
     |
     |  __lt__(self, value, /)
     |      Return self<value.
     |
     |  __ne__(self, value, /)
     |      Return self!=value.
     |
     |  __or__(self, value, /)
     |      Return self|value.
     |
     |  __repr__(self, /)
     |      Return repr(self).
     |
     |  __reversed__(self, /)
     |      Return a reverse iterator over the dict keys.
     |
     |  __ror__(self, value, /)
     |      Return value|self.
     |
     |  __setitem__(self, key, value, /)
     |      Set self[key] to value.
     |
     |  __sizeof__(...)
     |      D.__sizeof__() -> size of D in memory, in bytes
     |
     |  clear(...)
     |      D.clear() -> None.  Remove all items from D.
     |
     |  copy(...)
     |      D.copy() -> a shallow copy of D
     |
     |  get(self, key, default=None, /)
     |      Return the value for key if key is in the dictionary, else default.
     |
     |  items(...)
     |      D.items() -> a set-like object providing a view on D's items
     |
     |  keys(...)
     |      D.keys() -> a set-like object providing a view on D's keys
     |
     |  pop(...)
     |      D.pop(k[,d]) -> v, remove specified key and return the corresponding value.
     |
     |      If the key is not found, return the default if given; otherwise,
     |      raise a KeyError.
     |
     |  popitem(self, /)
     |      Remove and return a (key, value) pair as a 2-tuple.
     |
     |      Pairs are returned in LIFO (last-in, first-out) order.
     |      Raises KeyError if the dict is empty.
     |
     |  setdefault(self, key, default=None, /)
     |      Insert key with a value of default if key is not in the dictionary.
     |
     |      Return the value for key if key is in the dictionary, else default.
     |
     |  update(...)
     |      D.update([E, ]**F) -> None.  Update D from dict/iterable E and F.
     |      If E is present and has a .keys() method, then does:  for k in E: D[k] = E[k]
     |      If E is present and lacks a .keys() method, then does:  for k, v in E: D[k] = v
     |      In either case, this is followed by: for k in F:  D[k] = F[k]
     |
     |  values(...)
     |      D.values() -> an object providing a view on D's values
     |
     |  ----------------------------------------------------------------------
     |  Class methods inherited from builtins.dict:
     |
     |  __class_getitem__(...) from typing._TypedDictMeta
     |      See PEP 585
     |
     |  fromkeys(iterable, value=None, /) from typing._TypedDictMeta
     |      Create a new dictionary with keys from iterable and values set to value.
     |
     |  ----------------------------------------------------------------------
     |  Static methods inherited from builtins.dict:
     |
     |  __new__(*args, **kwargs) from builtins.type
     |      Create and return a new object.  See help(type) for accurate signature.
     |
     |  ----------------------------------------------------------------------
     |  Data and other attributes inherited from builtins.dict:
     |
     |  __hash__ = None

    class SoundServiceClient(pykos.services.AsyncClientBase)
     |  SoundServiceClient(channel: grpc.aio._base_channel.Channel) -> None
     |
     |  Client for the SoundService.
     |
     |  This service allows playing audio through speakers and recording from microphones.
     |
     |  Method resolution order:
     |      SoundServiceClient
     |      pykos.services.AsyncClientBase
     |      abc.ABC
     |      builtins.object
     |
     |  Methods defined here:
     |
     |  __init__(self, channel: grpc.aio._base_channel.Channel) -> None
     |      Initialize the sound service client.
     |
     |      Args:
     |          channel: gRPC channel to use for communication.
     |
     |  async get_audio_info(self) -> sound.AudioInfo
     |      Get information about audio capabilities.
     |
     |      Returns:
     |          AudioInfo containing playback and recording capabilities.
     |
     |  async play_audio(self, audio_iterator: AsyncIterator[bytes], **kwargs: Unpack[sound.AudioConfig]) -> kos.common_pb2.ActionResponse
     |      Stream PCM audio data to the speaker.
     |
     |      Args:
     |          audio_iterator: Iterator yielding chunks of PCM audio data
     |          **kwargs: Audio configuration parameters
     |              sample_rate: Sample rate in Hz (e.g., 44100)
     |              bit_depth: Bit depth (e.g., 16)
     |              channels: Number of channels (1 for mono, 2 for stereo)
     |
     |      Returns:
     |          ActionResponse indicating success/failure of the playback operation.
     |
     |      Example:
     |          >>> config = AudioConfig(sample_rate=44100, bit_depth=16, channels=2)
     |          >>> with open('audio.raw', 'rb') as f:
     |          ...     def chunks():
     |          ...         while chunk := f.read(4096):
     |          ...             yield chunk
     |          ...     response = client.play_audio(chunks(), config)
     |
     |  async record_audio(self, duration_ms: int = 0, **kwargs: Unpack[sound.AudioConfig]) -> AsyncGenerator[bytes, NoneType]
     |      Record PCM audio data from the microphone.
     |
     |      Args:
     |          duration_ms: Recording duration in milliseconds (0 for continuous)
     |          **kwargs: Audio configuration parameters
     |              sample_rate: Sample rate in Hz (e.g., 44100)
     |              bit_depth: Bit depth (e.g., 16)
     |              channels: Number of channels (1 for mono, 2 for stereo)
     |
     |      Yields:
     |          Chunks of PCM audio data.
     |
     |      Example:
     |          >>> config = AudioConfig(sample_rate=44100, bit_depth=16, channels=1)
     |          >>> with open('recording.raw', 'wb') as f:
     |          ...     for chunk in client.record_audio(duration_ms=5000, **config):
     |          ...         f.write(chunk)
     |
     |  async stop_recording(self) -> kos.common_pb2.ActionResponse
     |      Stop an ongoing recording session.
     |
     |      Returns:
     |          ActionResponse indicating success/failure of the stop operation.
     |
     |  ----------------------------------------------------------------------
     |  Data and other attributes defined here:
     |
     |  __abstractmethods__ = frozenset()
     |
     |  ----------------------------------------------------------------------
     |  Data descriptors inherited from pykos.services.AsyncClientBase:
     |
     |  __dict__
     |      dictionary for instance variables
     |
     |  __weakref__
     |      list of weak references to the object

DATA
    AsyncGenerator = typing.AsyncGenerator
        A generic version of collections.abc.AsyncGenerator.

    AsyncIterator = typing.AsyncIterator
        A generic version of collections.abc.AsyncIterator.

    NotRequired = typing.NotRequired
        Special typing construct to mark a TypedDict key as potentially missing.

        For example::

            class Movie(TypedDict):
                title: str
                year: NotRequired[int]

            m = Movie(
                title='The Matrix',  # typechecker error if key is omitted
                year=1999,
            )

    Unpack = typing.Unpack
        Type unpack operator.

        The type unpack operator takes the child types from some container type,
        such as `tuple[int, str]` or a `TypeVarTuple`, and 'pulls them out'.

        For example::

            # For some generic class `Foo`:
            Foo[Unpack[tuple[int, str]]]  # Equivalent to Foo[int, str]

            Ts = TypeVarTuple('Ts')
            # Specifies that `Bar` is generic in an arbitrary number of types.
            # (Think of `Ts` as a tuple of an arbitrary number of individual
            #  `TypeVar`s, which the `Unpack` is 'pulling out' directly into the
            #  `Generic[]`.)
            class Bar(Generic[Unpack[Ts]]): ...
            Bar[int]  # Valid
            Bar[int, str]  # Also valid

        From Python 3.11, this can also be done using the `*` operator::

            Foo[*tuple[int, str]]
            class Bar(Generic[*Ts]): ...

        And from Python 3.12, it can be done using built-in syntax for generics::

            Foo[*tuple[int, str]]
            class Bar[*Ts]: ...

        The operator can also be used along with a `TypedDict` to annotate
        `**kwargs` in a function signature::

            class Movie(TypedDict):
                name: str
                year: int

            # This function expects two keyword arguments - *name* of type `str` and
            # *year* of type `int`.
## Function `foo`

```python
            def foo(**kwargs: Unpack[Movie]): ...
```

        Note that there is only some runtime checking of this operator. Not
        everything the runtime allows may be accepted by static type checkers.

        For more information, see PEPs 646 and 692.

FILE
    /Users/verdakorzeniewski/kscale/kos/kos-py/pykos/services/sound.py



