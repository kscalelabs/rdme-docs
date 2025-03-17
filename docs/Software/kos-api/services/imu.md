---
title: imu
---

# imu

#### Help on module imu


NAME
    imu - IMU service client.

CLASSES
    builtins.dict(builtins.object)
        ZeroIMURequest
    builtins.object
        CalibrationMetadata
        CalibrationStatus
    google.protobuf.message.Message(builtins.object)
        kos.imu_pb2.CalibrateIMUMetadata(google.protobuf.pyext._message.CMessage, google.protobuf.message.Message)
    google.protobuf.pyext._message.CMessage(builtins.object)
        kos.imu_pb2.CalibrateIMUMetadata(google.protobuf.pyext._message.CMessage, google.protobuf.message.Message)
    pykos.services.AsyncClientBase(abc.ABC)
        IMUServiceClient

    class CalibrateIMUMetadata(google.protobuf.pyext._message.CMessage, google.protobuf.message.Message)
     |  Method resolution order:
     |      CalibrateIMUMetadata
     |      google.protobuf.pyext._message.CMessage
     |      google.protobuf.message.Message
     |      builtins.object
     |
     |  Data descriptors defined here:
     |
     |  status
     |      Field kos.imu.CalibrateIMUMetadata.status
     |
     |  ----------------------------------------------------------------------
     |  Data and other attributes defined here:
     |
     |  DESCRIPTOR = <google.protobuf.pyext._message.MessageDescriptor object>
     |
     |  ----------------------------------------------------------------------
     |  Methods inherited from google.protobuf.pyext._message.CMessage:
     |
     |  ByteSize(...)
     |      Returns the size of the message in bytes.
     |
     |  Clear(...)
     |      Clears the message.
     |
     |  ClearExtension(...)
     |      Clears a message field.
     |
     |  ClearField(...)
     |      Clears a message field.
     |
     |  CopyFrom(...)
     |      Copies a protocol message into the current message.
     |
     |  DiscardUnknownFields(...)
     |      Discards the unknown fields.
     |
     |  FindInitializationErrors(...)
     |      Finds unset required fields.
     |
     |  HasExtension(...)
     |      Checks if a message field is set.
     |
     |  HasField(...)
     |      Checks if a message field is set.
     |
     |  IsInitialized(...)
     |      Checks if all required fields of a protocol message are set.
     |
     |  ListFields(...)
     |      Lists all set fields of a message.
     |
     |  MergeFrom(...)
     |      Merges a protocol message into the current message.
     |
     |  MergeFromString(...)
     |      Merges a serialized message into the current message.
     |
     |  ParseFromString(...)
     |      Parses a serialized message into the current message.
     |
     |  SerializePartialToString(...)
     |      Serializes the message to a string, even if it isn't initialized.
     |
     |  SerializeToString(...)
     |      Serializes the message to a string, only for initialized messages.
     |
     |  SetInParent(...)
     |      Sets the has bit of the given field in its parent message.
     |
     |  UnknownFields(...)
     |      Parse unknown field set
     |
     |  WhichOneof(...)
     |      Returns the name of the field set inside a oneof, or None if no field is set.
     |
     |  __deepcopy__(...)
     |      Makes a deep copy of the class.
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
     |  __gt__(self, value, /)
     |      Return self>value.
     |
     |  __init__(self, /, *args, **kwargs)
     |      Initialize self.  See help(type(self)) for accurate signature.
     |
     |  __le__(self, value, /)
     |      Return self<=value.
     |
     |  __lt__(self, value, /)
     |      Return self<value.
     |
     |  __ne__(self, value, /)
     |      Return self!=value.
     |
     |  __repr__(self, /)
     |      Return repr(self).
     |
     |  __str__(self, /)
     |      Return str(self).
     |
     |  __unicode__(...)
     |      Outputs a unicode representation of the message.
     |
     |  ----------------------------------------------------------------------
     |  Class methods inherited from google.protobuf.pyext._message.CMessage:
     |
     |  FromString(...) from google.protobuf.pyext.cpp_message.GeneratedProtocolMessageType
     |      Creates new method instance from given serialized data.
     |
     |  RegisterExtension(...) from google.protobuf.pyext.cpp_message.GeneratedProtocolMessageType
     |      Registers an extension with the current message.
     |
     |  ----------------------------------------------------------------------
     |  Static methods inherited from google.protobuf.pyext._message.CMessage:
     |
     |  __new__(*args, **kwargs) from google.protobuf.pyext._message.MessageMeta
     |      Create and return a new object.  See help(type) for accurate signature.
     |
     |  ----------------------------------------------------------------------
     |  Data descriptors inherited from google.protobuf.pyext._message.CMessage:
     |
     |  Extensions
     |      Extension dict
     |
     |  ----------------------------------------------------------------------
     |  Data and other attributes inherited from google.protobuf.pyext._message.CMessage:
     |
     |  __hash__ = None
     |
     |  ----------------------------------------------------------------------
     |  Methods inherited from google.protobuf.message.Message:
     |
     |  __getstate__(self)
     |      Support the pickle protocol.
     |
     |  __reduce__(self)
     |      Helper for pickle.
     |
     |  __setstate__(self, state)
     |      Support the pickle protocol.

    class CalibrationMetadata(builtins.object)
     |  CalibrationMetadata(metadata_any: google.protobuf.any_pb2.Any) -> None
     |
     |  Methods defined here:
     |
     |  __init__(self, metadata_any: google.protobuf.any_pb2.Any) -> None
     |      Initialize self.  See help(type(self)) for accurate signature.
     |
     |  __repr__(self) -> str
     |      Return repr(self).
     |
     |  __str__(self) -> str
     |      Return str(self).
     |
     |  decode_metadata(self, metadata_any: google.protobuf.any_pb2.Any) -> None
     |
     |  ----------------------------------------------------------------------
     |  Data descriptors defined here:
     |
     |  __dict__
     |      dictionary for instance variables
     |
     |  __weakref__
     |      list of weak references to the object

    class CalibrationStatus(builtins.object)
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
     |  FAILED = 'FAILED'
     |
     |  IN_PROGRESS = 'IN_PROGRESS'
     |
     |  SUCCEEDED = 'SUCCEEDED'

    class IMUServiceClient(pykos.services.AsyncClientBase)
     |  IMUServiceClient(channel: grpc.aio._base_channel.Channel) -> None
     |
     |  Client for the IMUService.
     |
     |  Method resolution order:
     |      IMUServiceClient
     |      pykos.services.AsyncClientBase
     |      abc.ABC
     |      builtins.object
     |
     |  Methods defined here:
     |
     |  __init__(self, channel: grpc.aio._base_channel.Channel) -> None
     |      Initialize self.  See help(type(self)) for accurate signature.
     |
     |  async calibrate(self) -> kos.imu_pb2.CalibrateIMUResponse
     |      Calibrate the IMU.
     |
     |      This starts a long-running calibration operation. The operation can be monitored
     |      using get_calibration_status().
     |
     |      Returns:
     |          CalibrationMetadata: Metadata about the calibration operation.
     |
     |  async get_euler_angles(self) -> kos.imu_pb2.EulerAnglesResponse
     |      Get the latest Euler angles.
     |
     |      Returns:
     |          EulerAnglesResponse: The latest Euler angles.
     |
     |  async get_imu_advanced_values(self) -> kos.imu_pb2.IMUAdvancedValuesResponse
     |      Get the latest IMU advanced values.
     |
     |      Returns:
     |          ImuAdvancedValuesResponse: The latest IMU advanced values.
     |
     |  async get_imu_values(self) -> kos.imu_pb2.IMUValuesResponse
     |      Get the latest IMU sensor values.
     |
     |      Returns:
     |          ImuValuesResponse: The latest IMU sensor values.
     |
     |  async get_quaternion(self) -> kos.imu_pb2.QuaternionResponse
     |      Get the latest quaternion.
     |
     |      Returns:
     |          QuaternionResponse: The latest quaternion.
     |
     |  async zero(self, duration: float = 1.0, **kwargs: Unpack[imu.ZeroIMURequest]) -> kos.common_pb2.ActionResponse
     |      Zero the IMU.
     |
     |      Example:
     |          >>> await zero(duration=1.0,
     |          ...     max_retries=3,
     |          ...     max_angular_error=1.0,
     |          ...     max_velocity=1.0,
     |          ...     max_acceleration=1.0
     |          ... )
     |
     |      Args:
     |          duration: Duration in seconds for zeroing operation
     |          **kwargs: Additional zeroing parameters that may include:
     |                   max_retries: Maximum number of retries
     |                   max_angular_error: Maximum angular error during zeroing
     |                   max_velocity: Maximum velocity during zeroing
     |                   max_acceleration: Maximum acceleration during zeroing
     |
     |      Returns:
     |          ActionResponse: The response from the zero operation.
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

    class ZeroIMURequest(builtins.dict)
     |  Method resolution order:
     |      ZeroIMURequest
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
     |  __annotations__ = {'max_acceleration': typing.NotRequired[float], 'max...
     |
     |  __optional_keys__ = frozenset({'max_acceleration', 'max_angular_error'...
     |
     |  __orig_bases__ = (<function TypedDict>,)
     |
     |  __required_keys__ = frozenset()
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

DATA
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
    /Users/verdakorzeniewski/kscale/kos/kos-py/pykos/services/imu.py



