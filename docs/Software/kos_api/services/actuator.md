---
title: actuator
---

# actuator

#### Help on module actuator


NAME
    actuator - Actuator service client.

CLASSES
    builtins.dict(builtins.object)
        ActuatorCommand
        ActuatorPosition
        ActuatorStateRequest
        ConfigureActuatorRequest
    builtins.object
        CalibrationMetadata
        CalibrationStatus
    google.protobuf.message.Message(builtins.object)
        kos.actuator_pb2.CalibrateActuatorMetadata(google.protobuf.pyext._message.CMessage, google.protobuf.message.Message)
    google.protobuf.pyext._message.CMessage(builtins.object)
        kos.actuator_pb2.CalibrateActuatorMetadata(google.protobuf.pyext._message.CMessage, google.protobuf.message.Message)
    pykos.services.AsyncClientBase(abc.ABC)
        ActuatorServiceClient

    class ActuatorCommand(builtins.dict)
     |  Method resolution order:
     |      ActuatorCommand
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
     |  __annotations__ = {'actuator_id': <class 'int'>, 'position': typing.No...
     |
     |  __optional_keys__ = frozenset({'position', 'torque', 'velocity'})
     |
     |  __orig_bases__ = (<function TypedDict>,)
     |
     |  __required_keys__ = frozenset({'actuator_id'})
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

    class ActuatorPosition(builtins.dict)
     |  Method resolution order:
     |      ActuatorPosition
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
     |  __annotations__ = {'actuator_id': <class 'int'>, 'position': <class 'f...
     |
     |  __optional_keys__ = frozenset()
     |
     |  __orig_bases__ = (<function TypedDict>,)
     |
     |  __required_keys__ = frozenset({'actuator_id', 'position'})
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

    class ActuatorServiceClient(pykos.services.AsyncClientBase)
     |  ActuatorServiceClient(channel: grpc.aio._base_channel.Channel) -> None
     |
     |  Client for the ActuatorService.
     |
     |  Method resolution order:
     |      ActuatorServiceClient
     |      pykos.services.AsyncClientBase
     |      abc.ABC
     |      builtins.object
     |
     |  Methods defined here:
     |
     |  __init__(self, channel: grpc.aio._base_channel.Channel) -> None
     |      Initialize self.  See help(type(self)) for accurate signature.
     |
     |  async calibrate(self, actuator_id: int) -> actuator.CalibrationMetadata
     |      Calibrate an actuator.
     |
     |  async command_actuators(self, commands: list[actuator.ActuatorCommand]) -> kos.actuator_pb2.CommandActuatorsResponse
     |      Command multiple actuators at once.
     |
     |      Example:
     |          >>> command_actuators([
     |          ...     {"actuator_id": 1, "position": 90.0, "velocity": 100.0, "torque": 1.0},
     |          ...     {"actuator_id": 2, "position": 180.0},
     |          ... ])
     |
     |      Args:
     |          commands: List of dictionaries containing actuator commands.
     |                   Each dict should have 'actuator_id' and optionally 'position',
     |                   'velocity', and 'torque'.
     |
     |      Returns:
     |          List of ActionResult objects indicating success/failure for each command.
     |
     |  async configure_actuator(self, **kwargs: Unpack[actuator.ConfigureActuatorRequest]) -> kos.common_pb2.ActionResult
     |      Configure an actuator's parameters.
     |
     |      Example:
     |          >>> configure_actuator(
     |          ...     actuator_id=1,
     |          ...     kp=1.0,
     |          ...     kd=0.1,
     |          ...     ki=0.01,
     |          ...     acceleration=2230,
     |          ...     max_torque=100.0,
     |          ...     protective_torque=None,
     |          ...     protection_time=None,
     |          ...     torque_enabled=True,
     |          ...     new_actuator_id=None,
     |          ...     zero_position=True,
     |          ... )
     |
     |          >>> configure_actuator(
     |          ...     actuator_id=2,
     |          ...     kp=1.0,
     |          ...     kd=0.1,
     |          ...     torque_enabled=True,
     |          ... )
     |
     |      Args:
     |          actuator_id: ID of the actuator to configure
     |          **kwargs: Configuration parameters that may include:
     |                   kp, kd, ki, max_torque, protective_torque,
     |                   protection_time, torque_enabled, new_actuator_id
     |
     |      Returns:
     |          ActionResponse indicating success/failure
     |
     |  async get_actuators_state(self, actuator_ids: list[int] | None = None) -> kos.actuator_pb2.GetActuatorsStateResponse
     |      Get the state of multiple actuators.
     |
     |      Example:
     |          >>> get_actuators_state([1, 2])
     |
     |      Args:
     |          actuator_ids: List of actuator IDs to query. If None, gets state of all actuators.
     |
     |      Returns:
     |          List of ActuatorStateResponse objects containing the state information
     |
     |  async get_calibration_status(self, actuator_id: int) -> str | None
     |      Get the calibration status of an actuator.
     |
     |  async move_to_position(self, positions: list[actuator.ActuatorPosition], num_seconds: float, configure_actuators: list[actuator.ConfigureActuatorRequest] | None = None, commands_per_second: int = 10, torque_enabled: bool | None = None) -> None
     |      Helper function for moving actuators to a target position.
     |
     |      This first reads the current position of the actuators, then moves them
     |      to the target positions at a rate of `commands_per_second` commands per
     |      second.
     |
     |      We can additionally use this command to safely configure the actuator
     |      PD parameters after setting the target position to the current position.
     |
     |      Args:
     |          positions: The actuator target positions.
     |          num_seconds: How long to take the actuators to move to the target
     |              positions.
     |          configure_actuators: List of dictionaries containing actuator
     |              configuration parameters.
     |          commands_per_second: How many commands to send per second.
     |          torque_enabled: Whether to enable torque for the actuators.
     |
     |  async zero_actuators(self, actuator_id: int, zero_position: float, configure_actuator: actuator.ConfigureActuatorRequest | None = None, target_velocity: float = 0.25, commands_per_second: int = 10, move_back_seconds: float = 3.0) -> None
     |      Helper method for zeroing an actuator.
     |
     |      This function works to zero the actuator against an endstop, by moving
     |      the actuator until it reaches that endstop, then moving it back a small
     |      amount.
     |
     |      We can choose which endstop to zero against by setting the sign of
     |      `zero_position`. If it is positive, then we rotate counterclockwise
     |      until we reach an endstop, then back by this amount. If it is negative,
     |      then we rotate clockwise until we reach an endstop, then back by this
     |      amount.
     |
     |      Args:
     |          actuator_id: The ID of the actuator to zero.
     |          zero_position: The position to move the actuator back by after
     |              reaching the endstop.
     |          configure_actuator: Configuration parameters to set on the actuator
     |              before zeroing.
     |          target_velocity: The velocity to move the actuator at.
     |          commands_per_second: How many commands to send per second.
     |          move_back_seconds: How long to move the actuator back by after
     |              reaching the endstop.
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

    class ActuatorStateRequest(builtins.dict)
     |  Method resolution order:
     |      ActuatorStateRequest
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
     |  __annotations__ = {'actuator_ids': list[int]}
     |
     |  __optional_keys__ = frozenset()
     |
     |  __orig_bases__ = (<function TypedDict>,)
     |
     |  __required_keys__ = frozenset({'actuator_ids'})
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

    class CalibrateActuatorMetadata(google.protobuf.pyext._message.CMessage, google.protobuf.message.Message)
     |  Method resolution order:
     |      CalibrateActuatorMetadata
     |      google.protobuf.pyext._message.CMessage
     |      google.protobuf.message.Message
     |      builtins.object
     |
     |  Data descriptors defined here:
     |
     |  actuator_id
     |      Field kos.actuator.CalibrateActuatorMetadata.actuator_id
     |
     |  status
     |      Field kos.actuator.CalibrateActuatorMetadata.status
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
     |  Calibrated = 'calibrated'
     |
     |  Calibrating = 'calibrating'
     |
     |  Timeout = 'timeout'

    class ConfigureActuatorRequest(builtins.dict)
     |  Method resolution order:
     |      ConfigureActuatorRequest
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
     |  __annotations__ = {'acceleration': typing.NotRequired[float], 'actuato...
     |
     |  __optional_keys__ = frozenset({'acceleration', 'kd', 'ki', 'kp', 'max_...
     |
     |  __orig_bases__ = (<function TypedDict>,)
     |
     |  __required_keys__ = frozenset({'actuator_id'})
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
    /Users/verdakorzeniewski/kscale/kos/kos-py/pykos/services/actuator.py



