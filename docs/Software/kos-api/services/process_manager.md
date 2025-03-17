---
title: process_manager
---

# process_manager

Help on module process_manager:

NAME
    process_manager - Process manager service client.

CLASSES
    google.protobuf.message.Message(builtins.object)
        kos.process_manager_pb2.KClipStartRequest(google.protobuf.pyext._message.CMessage, google.protobuf.message.Message)
    google.protobuf.pyext._message.CMessage(builtins.object)
        kos.process_manager_pb2.KClipStartRequest(google.protobuf.pyext._message.CMessage, google.protobuf.message.Message)
    pykos.services.AsyncClientBase(abc.ABC)
        ProcessManagerServiceClient

    class KClipStartRequest(google.protobuf.pyext._message.CMessage, google.protobuf.message.Message)
     |  Method resolution order:
     |      KClipStartRequest
     |      google.protobuf.pyext._message.CMessage
     |      google.protobuf.message.Message
     |      builtins.object
     |
     |  Data descriptors defined here:
     |
     |  action
     |      Field kos.processmanager.KClipStartRequest.action
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

    class ProcessManagerServiceClient(pykos.services.AsyncClientBase)
     |  ProcessManagerServiceClient(channel: grpc.aio._base_channel.Channel) -> None
     |
     |  Client for the ProcessManagerService.
     |
     |  Method resolution order:
     |      ProcessManagerServiceClient
     |      pykos.services.AsyncClientBase
     |      abc.ABC
     |      builtins.object
     |
     |  Methods defined here:
     |
     |  __init__(self, channel: grpc.aio._base_channel.Channel) -> None
     |      Initialize self.  See help(type(self)) for accurate signature.
     |
     |  async start_kclip(self, action: str) -> kos.process_manager_pb2.KClipStartResponse
     |      Start KClip recording.
     |
     |      Args:
     |          action: The action string for the KClip request
     |
     |      Returns:
     |          The response from the server.
     |
     |  async stop_kclip(self, request: google.protobuf.empty_pb2.Empty = ) -> kos.process_manager_pb2.KClipStopResponse
     |      Stop KClip recording.
     |
     |      Returns:
     |          The response from the server.
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

FILE
    /Users/verdakorzeniewski/kscale/kos/kos-py/pykos/services/process_manager.py



