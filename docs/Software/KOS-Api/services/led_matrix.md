# LED Matrix Service

The LED Matrix Service allows control of an LED matrix display attached to the device, supporting various image formats and animations.

## Classes

### MatrixInfo (TypedDict)

Information about the LED matrix hardware capabilities.

#### Fields

- **width**: int - Width of the matrix in pixels
- **height**: int - Height of the matrix in pixels
- **brightness_levels**: int - Number of brightness levels supported (1 for binary on/off)
- **color_capable**: bool - Whether the matrix supports color
- **bits_per_pixel**: int - Number of bits used to represent each pixel
- **error**: NotRequired[Error | None] - Optional error information

### ImageData (TypedDict)

Image data to be displayed on the LED matrix.

#### Fields

- **buffer**: bytes - Raw image data bytes
- **width**: int - Image width in pixels
- **height**: int - Image height in pixels
- **format**: str - Pixel format specification (e.g. 'RGB888', 'BGR888', 'RGB565', 'MONO8')
- **brightness**: int - Global brightness level (0-255)

### LEDMatrixServiceClient (AsyncClientBase)

Client for interacting with the LED Matrix Service.

#### Methods

##### `__init__(self, channel: grpc.aio.Channel)`

Initialize the LED matrix service client with a gRPC channel.

##### `get_matrix_info(self) -> MatrixInfo`

Get information about the connected LED matrix.

**Returns:**
- MatrixInfo containing the matrix specifications

**Example:**
```python
info = await led_matrix.get_matrix_info()
print(f"LED Matrix: {info.width}x{info.height} pixels")
print(f"Color capable: {info.color_capable}")
```

##### `clear(self) -> ActionResult`

Clear the LED matrix display (turn off all LEDs).

**Returns:**
- ActionResult indicating success/failure

**Example:**
```python
await led_matrix.clear()
```

##### `set_brightness(self, brightness: int) -> ActionResult`

Set the global brightness level of the LED matrix.

**Parameters:**
- brightness: Brightness level (0-255)

**Returns:**
- ActionResult indicating success/failure

**Example:**
```python
await led_matrix.set_brightness(128)  # 50% brightness
```

##### `display_image(self, image_data: ImageData) -> ActionResult`

Display an image on the LED matrix.

**Parameters:**
- image_data: Image data to display (see ImageData fields)

**Returns:**
- ActionResult indicating success/failure

**Example:**
```python
# Create a red square image
width, height = 8, 8
pixels = bytes([255, 0, 0] * width * height)  # RGB888 format

await led_matrix.display_image({
    "buffer": pixels,
    "width": width,
    "height": height,
    "format": "RGB888",
    "brightness": 255
})
```

##### `display_animation(self, frames: list[ImageData], frame_duration_ms: int, loop: bool = False) -> ActionResult`

Display an animation on the LED matrix.

**Parameters:**
- frames: List of image frames to display
- frame_duration_ms: Duration to display each frame in milliseconds
- loop: Whether to continuously loop the animation

**Returns:**
- ActionResult indicating success/failure

**Example:**
```python
# Create a simple 2-frame animation (red and blue squares)
width, height = 8, 8
red_frame = {
    "buffer": bytes([255, 0, 0] * width * height),
    "width": width, "height": height,
    "format": "RGB888", "brightness": 255
}
blue_frame = {
    "buffer": bytes([0, 0, 255] * width * height),
    "width": width, "height": height,
    "format": "RGB888", "brightness": 255
}

await led_matrix.display_animation(
    frames=[red_frame, blue_frame],
    frame_duration_ms=500,  # 0.5 seconds per frame
    loop=True
)
```

##### `stop_animation(self) -> ActionResult`

Stop a currently playing animation.

**Returns:**
- ActionResult indicating success/failure

**Example:**
```python
await led_matrix.stop_animation()
```

##### `draw_text(self, text: str, color: list[int], font_size: int = 1, scroll: bool = False, scroll_speed_ms: int = 100) -> ActionResult`

Draw text on the LED matrix.

**Parameters:**
- text: Text string to display
- color: RGB color as a list [r, g, b] with values 0-255
- font_size: Font size multiplier (1 = smallest)
- scroll: Whether to scroll the text
- scroll_speed_ms: Scrolling speed in milliseconds per pixel shift

**Returns:**
- ActionResult indicating success/failure

**Example:**
```python
# Display scrolling yellow text
await led_matrix.draw_text(
    text="Hello World!",
    color=[255, 255, 0],  # Yellow
    font_size=1,
    scroll=True,
    scroll_speed_ms=80
)
```