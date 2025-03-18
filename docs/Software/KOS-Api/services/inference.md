# inference

Inference service client.

## Classes

### ForwardResponse (T, y, p, e, d, D, i, c, t)

Response from running model inference.

**Arguments:**
- *outputs*: Dictionary mapping tensor names to output tensors
- *error*: Optional error information if inference failed

### GetModelsInfoResponse (T, y, p, e, d, D, i, c, t)

Response containing information about available models.

### InferenceServiceClient (A, s, y, n, c, C, l, i, e, n, t, B, a, s, e)

Client for the InferenceService.

    This service allows uploading models and running inference on them.

#### __init__self, channel: grpc.aio.Channel

Initialize the inference service client.

**Arguments:**
- *channel*: gRPC channel to use for communication.

#### forwardself, model_uid: str, inputs: dict[str, Tensor]

Run inference using a specified model.

**Arguments:**
- *model_uid*: The UID of the model to use for inference.
- *inputs*: Dictionary mapping tensor names to tensors.

**Returns:**
            ForwardResponse containing:
                outputs: Dictionary mapping tensor names to output tensors
                error: Optional error information if inference failed

#### get_models_infoself, model_uids: list[str] | None = None

Get information about available models.

**Arguments:**
- *model_uids*: Optional list of specific model UIDs to get info for.
                       If None, returns info for all models.

**Returns:**
            GetModelsInfoResponse containing:
                models: List of ModelInfo objects
                error: Optional error information if fetching failed

#### load_modelsself, uids: list[str]

Load models from the robot's filesystem.

**Arguments:**
- *uids*: List of model UIDs to load.

**Returns:**
            LoadModelsResponse containing information about the loaded models.

#### unload_modelsself, uids: list[str]

Unload models from the robot's filesystem.

**Arguments:**
- *uids*: List of model UIDs to unload.

**Returns:**
            ActionResponse indicating success/failure of the unload operation.

#### upload_modelself, model_data: bytes, metadata: ModelMetadata | None = None

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

### ModelInfo (T, y, p, e, d, D, i, c, t)

Information about a model.

**Arguments:**
- *uid*: Model UID (assigned by server)
- *metadata*: Model metadata
- *input_specs*: Expected input tensor specifications
- *output_specs*: Expected output tensor specifications
- *description*: str

### ModelMetadata (T, y, p, e, d, D, i, c, t)

Model metadata for uploading models.

    All fields are optional and can be used to provide additional information about the model.

### Tensor (T, y, p, e, d, D, i, c, t)

A tensor containing data.

**Arguments:**
- *values*: Tensor values in row-major order
- *shape*: List of dimension information

### TensorDimension (T, y, p, e, d, D, i, c, t)

Information about a tensor dimension.

**Arguments:**
- *size*: Size of this dimension
- *name*: Name of this dimension (e.g., "batch", "channels", "height")
- *dynamic*: Whether this dimension can vary (e.g., batch size)
