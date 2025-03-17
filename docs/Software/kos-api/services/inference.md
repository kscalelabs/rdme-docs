# inference

Inference service client.

## Classes

### ForwardResponse (dict)

Response from running model inference.

**Arguments:**
- *outputs*: Dictionary mapping tensor names to output tensors
- *error*: Optional error information if inference failed

### GetModelsInfoResponse (dict)

Response containing information about available models.

### InferenceServiceClient (AsyncClientBase)

Client for the InferenceService.

This service allows uploading models and running inference on them.

#### __init__(self, channel: grpc.aio._base_channel.Channel) -> None

Initialize the inference service client.

**Arguments:**
- *channel*: gRPC channel to use for communication.

#### forward(self, model_uid: str, inputs: dict[str, inference.Tensor]) -> inference.ForwardResponse

Run inference using a specified model.

**Arguments:**
- *model_uid*: The UID of the model to use for inference.
- *inputs*: Dictionary mapping tensor names to tensors.

**Returns:**
    ForwardResponse containing:
        outputs: Dictionary mapping tensor names to output tensors
        error: Optional error information if inference failed

#### get_models_info(self, model_uids: list[str] | None = None) -> inference.GetModelsInfoResponse

Get information about available models.

**Arguments:**
- *model_uids*: Optional list of specific model UIDs to get info for.
               If None, returns info for all models.

**Returns:**
    GetModelsInfoResponse containing:
        models: List of ModelInfo objects
        error: Optional error information if fetching failed

#### load_models(self, uids: list[str]) -> kos.inference_pb2.LoadModelsResponse

Load models from the robot's filesystem.

**Arguments:**
- *uids*: List of model UIDs to load.

**Returns:**
    LoadModelsResponse containing information about the loaded models.

#### unload_models(self, uids: list[str]) -> kos.common_pb2.ActionResponse

Unload models from the robot's filesystem.

**Arguments:**
- *uids*: List of model UIDs to unload.

**Returns:**
    ActionResponse indicating success/failure of the unload operation.

#### upload_model(self, model_data: bytes, metadata: inference.ModelMetadata | None = None) -> kos.inference_pb2.UploadModelResponse

Upload a model to the robot.

Example:
```python
>>> client.upload_model(model_data,
... metadata={"model_name": "MyModel",
... "model_description": "A model for inference",
... "model_version": "1.0.0",
... "model_author": "John Doe"})

```
**Arguments:**
- *model_data*: The binary model data to upload.
- *metadata*: Optional metadata about the model that can include:
- *model_name*: Name of the model
- *model_description*: Description of the model
- *model_version*: Version of the model
- *model_author*: Author of the model

**Returns:**
    UploadModelResponse containing the model UID and any error information.

### ModelInfo (dict)

Information about a model.

**Arguments:**
- *uid*: Model UID (assigned by server)
- *metadata*: Model metadata
- *input_specs*: Expected input tensor specifications
- *output_specs*: Expected output tensor specifications
- *description*: str

### ModelMetadata (dict)

Model metadata for uploading models.

All fields are optional and can be used to provide additional information about the model.

### Tensor (dict)

A tensor containing data.

**Arguments:**
- *values*: Tensor values in row-major order
- *shape*: List of dimension information

### TensorDimension (dict)

Information about a tensor dimension.

**Arguments:**
- *size*: Size of this dimension
- *name*: Name of this dimension (e.g., "batch", "channels", "height")
- *dynamic*: Whether this dimension can vary (e.g., batch size)
