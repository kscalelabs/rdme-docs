# Inference Service

The Inference Service provides model loading and neural network inference capabilities, supporting a variety of model formats and tensor operations.

## Classes

### ModelMetadata (TypedDict)

Model metadata for model management.

#### Fields

- **model_name**: NotRequired[str | None] - Name of the model
- **model_description**: NotRequired[str | None] - Description of the model's purpose or functionality
- **model_version**: NotRequired[str | None] - Version identifier for the model
- **model_author**: NotRequired[str | None] - Author of the model

### TensorDimension (TypedDict)

Information about a single dimension in a tensor.

#### Fields

- **size**: int - Size of this dimension
- **name**: str - Semantic name of this dimension (e.g., "batch", "channels", "height")
- **dynamic**: bool - Whether this dimension can vary in size (e.g., batch size)

### Tensor (TypedDict)

A tensor containing data for model inputs or outputs.

#### Fields

- **values**: list[float] - Tensor values in row-major order
- **shape**: list[TensorDimension] - Shape information for the tensor

### ForwardResponse (TypedDict)

Response from running model inference.

#### Fields

- **outputs**: dict[str, Tensor] - Dictionary mapping tensor names to output tensors
- **error**: NotRequired[Error | None] - Optional error information if inference failed

### ModelInfo (TypedDict)

Information about a loaded model.

#### Fields

- **uid**: str - Unique identifier for the model
- **metadata**: ModelMetadata - Additional model metadata
- **input_specs**: dict[str, Tensor] - Expected input tensor specifications
- **output_specs**: dict[str, Tensor] - Expected output tensor specifications 
- **description**: str - Human-readable description of the model

### GetModelsInfoResponse (TypedDict)

Response containing information about available models.

#### Fields

- **models**: list[ModelInfo] - List of available models
- **error**: NotRequired[Error | None] - Optional error information

### InferenceServiceClient (AsyncClientBase)

Client for interacting with the Inference Service.

#### Methods

##### `__init__(self, channel: grpc.aio.Channel)`

Initialize the inference service client with a gRPC channel.

##### `upload_model(self, model_path: str, model_format: str = "onnx", metadata: ModelMetadata = None) -> ModelInfo`

Upload a model to the inference service.

**Parameters:**
- model_path: Path to model file
- model_format: Format of the model file (e.g., "onnx", "tflite")
- metadata: Optional model metadata

**Returns:**
- ModelInfo containing information about the uploaded model

**Example:**
```python
model_info = await inference_client.upload_model(
    model_path="/path/to/model.onnx",
    model_format="onnx",
    metadata={
        "model_name": "my_classifier",
        "model_description": "Image classifier trained on ImageNet",
        "model_version": "1.0.0"
    }
)
print(f"Uploaded model UID: {model_info.uid}")
```

##### `get_models_info(self) -> GetModelsInfoResponse`

Get information about all available models.

**Returns:**
- Response containing list of available models

**Example:**
```python
response = await inference_client.get_models_info()
print(f"Available models: {len(response.models)}")
for model in response.models:
    print(f"- {model.metadata.model_name} (UID: {model.uid})")
```

##### `delete_model(self, model_uid: str) -> ActionResult`

Delete a model from the inference service.

**Parameters:**
- model_uid: Unique identifier of the model to delete

**Returns:**
- ActionResult indicating success/failure

**Example:**
```python
result = await inference_client.delete_model("model_12345")
```

##### `forward(self, model_uid: str, inputs: dict[str, Tensor]) -> ForwardResponse`

Run inference on the specified model.

**Parameters:**
- model_uid: Unique identifier of the model to use
- inputs: Dictionary mapping input names to tensor data

**Returns:**
- Response containing model outputs

**Example:**
```python
# Create a simple 1x3 input tensor
input_tensor = {
    "values": [0.1, 0.2, 0.3],
    "shape": [
        {"size": 1, "name": "batch", "dynamic": False},
        {"size": 3, "name": "features", "dynamic": False}
    ]
}

# Run inference
response = await inference_client.forward(
    model_uid="model_12345",
    inputs={"input": input_tensor}
)

# Process the output
output_tensor = response.outputs["output"]
print(f"Output values: {output_tensor.values}")
```

##### `preprocess_image(self, image_data: bytes, input_specs: dict[str, Tensor]) -> dict[str, Tensor]`

Preprocess an image for model input based on model specifications.

**Parameters:**
- image_data: Raw image data bytes
- input_specs: Model input specifications

**Returns:**
- Dictionary of preprocessed tensors ready for model input

**Example:**
```python
# Load an image
with open("image.jpg", "rb") as f:
    image_data = f.read()

# Get model info to find input specs
model_info = await inference_client.get_models_info()
target_model = model_info.models[0]

# Preprocess the image
inputs = await inference_client.preprocess_image(
    image_data=image_data, 
    input_specs=target_model.input_specs
)

# Run inference
result = await inference_client.forward(
    model_uid=target_model.uid,
    inputs=inputs
)
```

##### `get_model_statistics(self, model_uid: str) -> ModelStatistics`

Get performance statistics for a model.

**Parameters:**
- model_uid: Unique identifier of the model

**Returns:**
- Statistics including inference time, memory usage, etc.

**Example:**
```python
stats = await inference_client.get_model_statistics("model_12345")
print(f"Average inference time: {stats.avg_inference_time_ms}ms")
print(f"Memory usage: {stats.memory_usage_mb}MB")
```