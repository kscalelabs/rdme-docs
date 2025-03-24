---
title: ksim
excerpt: K-Scale's Mujoco-based framework for training policies in simulation
deprecated: false
hidden: false
metadata:
  robots: index
---
Welcome to `ksim`, K-Scale's Mujoco-based framework for training policies in simulation.

[https://github.com/kscalelabs/ksim](https://github.com/kscalelabs/ksim)

### Getting Started

To get started, run one of our [example scripts](https://github.com/kscalelabs/ksim/tree/master/examples) .

## Common Errors

### NaNs when running example policy

This manifests sometimes when you have an error like this:

`Registers are spilled to local memory in function`

We have observed this happening when training on RTX 4090s. To mitigate, disable Triton GEMM kernels:

```shell
export XLA_FLAGS='--xla_gpu_enable_latency_hiding_scheduler=true --xla_gpu_enable_triton_gemm=false'
```

Then, you may need to remove your JAX cache to trigger JAX to rebuild the kernels:

```shell
rm -r ~/.cache/jax/jaxcache
```