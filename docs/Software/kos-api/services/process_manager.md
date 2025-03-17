# process_manager

Process manager service client.

## Classes

### ProcessManagerServiceClient (AsyncClientBase)

Client for the ProcessManagerService.

#### __init__(self, channel: grpc.aio._base_channel.Channel) -> None


#### start_kclip(self, action: str) -> kos.process_manager_pb2.KClipStartResponse

Start KClip recording.

**Arguments:**
- *action*: The action string for the KClip request

**Returns:**
    The response from the server.

#### stop_kclip(self, request: google.protobuf.empty_pb2.Empty = ) -> kos.process_manager_pb2.KClipStopResponse

Stop KClip recording.

**Returns:**
    The response from the server.
