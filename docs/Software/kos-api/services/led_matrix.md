# led_matrix

LED Matrix service client.

## Classes

### ImageData (dict)

Image data to be written to the LED matrix.

**Arguments:**
- *buffer*: Raw image data bytes
- *width*: Image width in pixels
- *height*: Image height in pixels
- *format*: Pixel format specification (e.g. 'RGB888', 'BGR888', 'RGB565', 'MONO8')
- *brightness*: Global brightness level (0-255)

### LEDMatrixServiceClient (AsyncClientBase)

Client for the LEDMatrixService.

This service allows controlling an LED matrix display.

#### __init__(self, channel: grpc.aio._base_channel.Channel) -> None

Initialize the LED matrix service client.

**Arguments:**
- *channel*: gRPC channel to use for communication.

#### get_matrix_info(self) -> led_matrix.MatrixInfo

Get information about the LED matrix including dimensions and capabilities.

**Returns:**
    MatrixInfo containing:
        width: Width in pixels
        height: Height in pixels
        brightness_levels: Number of brightness levels supported
        color_capable: Whether the matrix supports color
        bits_per_pixel: Number of bits used to represent each pixel
        error: Optional error information

#### write_buffer(self, buffer: bytes) -> kos.common_pb2.ActionResponse

Write binary on/off states to the LED matrix.

The buffer should be width * height / 8 bytes long, where each bit
represents one LED's on/off state.

**Arguments:**
- *buffer*: Binary buffer containing LED states

**Returns:**
    ActionResponse indicating success/failure of the write operation.

#### write_color_buffer(self, **kwargs: Unpack[led_matrix.ImageData]) -> kos.common_pb2.ActionResponse

Write image data to the LED matrix.

**Arguments:**
- ***kwargs*: Image data containing the raw bytes, dimensions and format
- *buffer*: Raw image data bytes
- *width*: Image width in pixels
- *height*: Image height in pixels
- *format*: Pixel format specification (e.g. 'RGB888', 'BGR888', 'RGB565', 'MONO8')
- *brightness*: Global brightness level (0-255)

**Returns:**
    ActionResponse indicating success/failure of the write operation.

### MatrixInfo (dict)

Information about the LED matrix.

**Arguments:**
- *width*: Width in pixels
- *height*: Height in pixels
- *brightness_levels*: Number of brightness levels supported (1 for binary on/off)
- *color_capable*: Whether the matrix supports color
- *bits_per_pixel*: Number of bits used to represent each pixel
- *error*: Optional error information
