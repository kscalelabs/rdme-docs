---
title: K-Infer
excerpt: Inference library for running models
deprecated: false
hidden: false
metadata:
  robots: index
---
<Cards columns={2}>
  <Card title="Github" href="https://github.com/kscalelabs/kinfer" icon="fa-home" target="_blank">
    The main <code>kinfer</code> Github repository
  </Card>

  <Card title="Onnx Runtime" href="https://onnxruntime.ai" icon="fa-code" target="_blank">
    The Onnx runtime library documentation
  </Card>
</Cards>

`kinfer` is a package for doing inference on K-Scale models, by providing a standard interface for trained policies. This lets you take a trained policy, compile it to a `kinfer` model binary, and run the same binary in simulation and on a real robot.

Each `kinfer` model has three parts:

1. An `init` function, which initializes the model carry
2. A `step` function, which processes one computation step
3. Some additional `metadata` telling downstream implementations how to use the model input and outputs

The control loop for a `kinfer` model can be thought of as follows:

```python Python
carry = init() # Onnx graph
while True:
  model_input = get_model_input() # Implemented by provider
  model_output, carry = step(model_input, carry) # Onnx graph
  do_model_output(model_output) # Implemented by provider
  sleep()
```

## Dependencies

This requires `onnxruntime = 1.20.0`. The easiest way to install this is through `pip`, which will determine the correct shared library to use for your system:

```shell Shell
pip install 'onnxruntime==1.20.0'
```

After doing this, you need to set `ORT_DYLIB_PATH` to point to the dynamic library. This can be found using the following command:

```shell
python -c 'import onnxruntime as ort ; from pathlib import Path ; print(next((Path(ort.__file__).parent / "capi").glob("libonnxruntime.*")))'

export ORT_DYLIB_PATH=/path/to/libonnxruntime.[so,dylib]
```

The runtime will dynamically link to this path.