---
title: Troubleshooting
excerpt: Help troubleshooting common issues
deprecated: false
hidden: false
metadata:
  robots: index
---
## Onnx Runtime

If using Python, `kinfer` should automatically set the required `ORT_DYLIB_PATH` environment variable for you. However, when running the Rust binary directly, you will have to specify this yourself.

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