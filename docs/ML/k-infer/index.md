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

This provides a common interface for running models in simulation and on the real robot, making sim2real transfer straightforward.