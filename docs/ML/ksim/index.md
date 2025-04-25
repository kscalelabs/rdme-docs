---
title: ksim
excerpt: K-Scale's Mujoco-based framework for training policies in simulation
deprecated: false
hidden: false
metadata:
  title: ksim
  keywords:
    - mujoco
    - simulation
    - policies
  robots: index
---
Welcome to `ksim`, a modular and robust framework for training policies in simulation.

<Image align="center" src="https://files.readme.io/42bf70f3cd26469792fe6474ee855580257f6e12aa1c0368196bf32b353adce5-individualImage.gif" />

See the framework source code on [Github](https://github.com/kscalelabs/ksim).

## Overview

KSim is designed to be modular, making it easy to implement new architectures, define bespoke domain randomizations, and
mix and match training objectives. Inspired by PyTorch Lightning's interface, training jobs are defined by a `Task`
class which specifies environment parameters, policy hooks, and training logic. KSim is built on top of the
[Mujoco](https://github.com/google-deepmind/mujoco) and [MJX](https://github.com/google-deepmind/mjx) physics engines,
and it uses [JAX](https://github.com/google/jax) for the underlying training logic. As such, KSim is built with parallel
training in mind and achieves high GPU utilization throughout training.

## Table of Contents

Want to learn more? Check out the following guides:

- [Quick Start](./quick_start.md)
- [Defining a Task](./task.md)
- [Environment Builders](./builders.md)
- [Troubleshooting](./troubleshooting.md)

## Contributing

We welcome contributions! Please see the [contributing guide](./contributing.md) for more information.

## License

`ksim` is released under the [MIT License](./LICENSE).

