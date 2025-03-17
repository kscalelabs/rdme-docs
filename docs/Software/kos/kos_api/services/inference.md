---
title: inference
---

# inference

#### Help on module inference


NAME
    inference - Inference service client.

CLASSES
    builtins.dict(builtins.object)
        ForwardResponse
        GetModelsInfoResponse
        ModelInfo
        ModelMetadata
        Tensor
        TensorDimension
    pykos.services.AsyncClientBase(abc.ABC)
        InferenceServiceClient

    class ForwardResponse(builtins.dict)
     |  Response from running model inference.
     |
     |  Args:
     |      outputs: Dictionary mapping tensor names to output tensors
     |      error: Optional error information if inference failed
     |
     |  Method resolution order:
     |      ForwardResponse
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
     |  __required_keys__ = frozenset({'outputs'})
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

    class GetModelsInfoResponse(builtins.dict)
     |  Response containing information about available models.
     |
     |  Method resolution order:
     |      GetModelsInfoResponse
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
     |  __required_keys__ = frozenset({'models'})
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

    class InferenceServiceClient(pykos.services.AsyncClientBase)
     |  InferenceServiceClient(channel: grpc.aio._base_channel.Channel) -> None
     |
     |  Client for the InferenceService.
     |
     |  This service allows uploading models and running inference on them.
     |
     |  Method resolution order:
     |      InferenceServiceClient
     |      pykos.services.AsyncClientBase
     |      abc.ABC
     |      builtins.object
     |
     |  Methods defined here:
     |
     |  __init__(self, channel: grpc.aio._base_channel.Channel) -> None
     |      Initialize the inference service client.
     |
     |      Args:
     |          channel: gRPC channel to use for communication.
     |
     |  async forward(self, model_uid: str, inputs: dict[str, inference.Tensor]) -> inference.ForwardResponse
     |      Run inference using a specified model.
     |
     |      Args:
     |          model_uid: The UID of the model to use for inference.
     |          inputs: Dictionary mapping tensor names to tensors.
     |
     |      Returns:
     |          ForwardResponse containing:
     |              outputs: Dictionary mapping tensor names to output tensors
     |              error: Optional error information if inference failed
     |
     |  async get_models_info(self, model_uids: list[str] | None = None) -> inference.GetModelsInfoResponse
     |      Get information about available models.
     |
     |      Args:
     |          model_uids: Optional list of specific model UIDs to get info for.
     |                     If None, returns info for all models.
     |
     |      Returns:
     |          GetModelsInfoResponse containing:
     |              models: List of ModelInfo objects
     |              error: Optional error information if fetching failed
     |
     |  async load_models(self, uids: list[str]) -> kos.inference_pb2.LoadModelsResponse
     |      Load models from the robot's filesystem.
     |
     |      Args:
     |          uids: List of model UIDs to load.
     |
     |      Returns:
     |          LoadModelsResponse containing information about the loaded models.
     |
     |  async unload_models(self, uids: list[str]) -> kos.common_pb2.ActionResponse
     |      Unload models from the robot's filesystem.
     |
     |      Args:
     |          uids: List of model UIDs to unload.
     |
     |      Returns:
     |          ActionResponse indicating success/failure of the unload operation.
     |
     |  async upload_model(self, model_data: bytes, metadata: inference.ModelMetadata | None = None) -> kos.inference_pb2.UploadModelResponse
     |      Upload a model to the robot.
     |
     |      Example:
     |      >>> client.upload_model(model_data,
     |      ... metadata={"model_name": "MyModel",
     |      ... "model_description": "A model for inference",
     |      ... "model_version": "1.0.0",
     |      ... "model_author": "John Doe"})
     |
     |      Args:
     |          model_data: The binary model data to upload.
     |          metadata: Optional metadata about the model that can include:
     |                   model_name: Name of the model
     |                   model_description: Description of the model
     |                   model_version: Version of the model
     |                   model_author: Author of the model
     |
     |      Returns:
     |          UploadModelResponse containing the model UID and any error information.
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

    class ModelInfo(builtins.dict)
     |  Information about a model.
     |
     |  Args:
     |      uid: Model UID (assigned by server)
     |      metadata: Model metadata
     |      input_specs: Expected input tensor specifications
     |      output_specs: Expected output tensor specifications
     |      description: str
     |
     |  Method resolution order:
     |      ModelInfo
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
     |  __annotations__ = {'description': <class 'str'>, 'input_specs': dict[s...
     |
     |  __optional_keys__ = frozenset()
     |
     |  __orig_bases__ = (<function TypedDict>,)
     |
     |  __required_keys__ = frozenset({'description', 'input_specs', 'metadata...
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

    class ModelMetadata(builtins.dict)
     |  Model metadata for uploading models.
     |
     |  All fields are optional and can be used to provide additional information about the model.
     |
     |  Method resolution order:
     |      ModelMetadata
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
     |  __annotations__ = {'model_author': typing.NotRequired[str | None], 'mo...
     |
     |  __optional_keys__ = frozenset({'model_author', 'model_description', 'm...
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

    class Tensor(builtins.dict)
     |  A tensor containing data.
     |
     |  Args:
     |      values: Tensor values in row-major order
     |      shape: List of dimension information
     |
     |  Method resolution order:
     |      Tensor
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
     |  __annotations__ = {'shape': list[inference.TensorDimension], 'values':...
     |
     |  __optional_keys__ = frozenset()
     |
     |  __orig_bases__ = (<function TypedDict>,)
     |
     |  __required_keys__ = frozenset({'shape', 'values'})
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

    class TensorDimension(builtins.dict)
     |  Information about a tensor dimension.
     |
     |  Args:
     |      size: Size of this dimension
     |      name: Name of this dimension (e.g., "batch", "channels", "height")
     |      dynamic: Whether this dimension can vary (e.g., batch size)
     |
     |  Method resolution order:
     |      TensorDimension
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
     |  __annotations__ = {'dynamic': <class 'bool'>, 'name': <class 'str'>, '...
     |
     |  __optional_keys__ = frozenset()
     |
     |  __orig_bases__ = (<function TypedDict>,)
     |
     |  __required_keys__ = frozenset({'dynamic', 'name', 'size'})
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

FILE
    /Users/verdakorzeniewski/kscale/kos/kos-py/pykos/services/inference.py



