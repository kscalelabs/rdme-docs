---
title: ksim
excerpt: K-Scale's Mujoco-based framework for training policies in simulation
deprecated: false
hidden: false
metadata:
  title: ksim
  robots: index
---
Welcome to `ksim`, K-Scale's Mujoco-based framework for training policies in simulation.

<Image align="center" src="https://files.readme.io/62a1fb382d2b181d46516cf14909b38ea0359a41cb6d1ba01988ad8f38b2ab77-policy.gif" />

See the framework source code on [Github](https://github.com/kscalelabs/ksim).

## Getting Started

To install `ksim`, simply run:

```
pip install ksim
```

Make sure you have [installed Jax correctly](https://docs.jax.dev/en/latest/installation.html)  for your system.

We recommend using `conda` instead of `uv` as a virtual environment manager for now, because we've observed weird issues with `mjpython` with `uv` on MacOS.

After installation, run one of our [example scripts](https://github.com/kscalelabs/ksim/tree/master/examples) .

## Terminology

The following terminology is relevant to understanding RL tasks.

* `Trajector`: includes obs, command, action, and done. The latter is\
  conditioned on the trajectory produced by the action.
* Dataset: a set of `Trajectory`s used for training an RL update. Fully defined by\
  `num_env_states_per_minibatch * num_minibatches`.
* Minibatch: a subset of the dataset used for training an RL update. Updates are\
  performed per minibatch.
* Minibatch size: the number of environment states in each minibatch.
* Epoch: number of full passes through the current training dataset.
* Num Envs: the amount of parallel environments to run. Because of automatic\
  resetting, this should not affect the batch math (in expectation).

### Variable Naming Conventions

Please use these units in the suffixes of variable names. For PyTrees, assume\
consistency of all dimensions except `L`. If including the timestampe would
help someone understand the variable, do the dimension suffix first, then the
timestamp suffix. (e.g. `mjx_data_L_0`). If it helps, specify return units in
function docstrings.

Dimension suffixes:

* `D`: dimension of environment states in the dataset.
* `B`: dimension of environment states in each minibatch.
* `T`: the time dimension during rollout.
* `E`: the env dimension during rollout.
* `L`: leaf dimension of a pytree (e.g. joint position vector size in an obs),\
  should not be used if the variable's final dimension is a scalar.

Timestamp suffixes:

* `t`: current timestep
* `t_plus_1`: next timestep
* `t_minus_1`: previous timestep
* `t_0`: initial timestep
* `t_f`: final timestep

These should absolutely be annotated:

* `mjx.Data`
* `mjx.Model`
* Everything relevant to `Trajectory` (e.g. `obs`, `command`, `action`, etc.)

## Troubleshooting

### Headless Systems

When you try to render a trajectory while on a headless system, you may get an error like the following:

```bash
mujoco.FatalError: an OpenGL platform library has not been loaded into this process, this most likely means that a valid OpenGL context has not been created before mjr_makeContext was called
```

The fix is to create a virtual display:

```bash
Xvfb :100 -ac &
PID1=$!
export DISPLAY=:100.0
```

You may also need to tell MuJoCo to use GPU accelerated off-screen rendering via

```
export MUJOCO_GL="egl"
```

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

We've found that removing the cache can fix a number of otherwise-mysterious errors.