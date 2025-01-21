---
title: Actuators
excerpt: >-
  We have developed Python and Rust packages to make it easy to control our
  robot's actuators.
deprecated: false
hidden: false
metadata:
  robots: index
---
We have developed Python and Rust packages to make it easy to control our robot's actuators.

<br />

## Installation

The package can easily be installed from PyPI using the command:

```bash
sudo apt install pkg-config libudev-dev  # If not installed
pip install actuator
```

Alternatively, to install the bleeding edge version from Github, use the command:

```bash
pip install 'actuator @ git+https://github.com/kscalelabs/actuator.git@master'
```

<br />

Actuators are the most important component of a robot. In this guide, we will walk you through the actuators that we use in our robot and conventions we use to connect to them.

## Specs

Our general-purpose robot uses the Robstride series of actuators.

| Actuator                                                   | Torque | Voltage | Encoders       |
| ---------------------------------------------------------- | ------ | ------- | -------------- |
| [Robstride 00](https://robstride.com/products/robStride00) | 14 Nm  | 48 V    | Dual-encoder   |
| [Robstride 01](https://robstride.com/products/robStride01) | 17 Nm  | 36 V    | Single-encoder |
| [Robstride 02](https://robstride.com/products/robStride02) | 17 Nm  | 48 V    | Dual-encoder   |
| [Robstride 03](https://robstride.com/products/robStride03) | 60 Nm  | 48 V    | Dual-encoder   |
| [Robstride 04](https://robstride.com/products/robStride04) | 120 Nm | 48 V    | Dual-encoder   |