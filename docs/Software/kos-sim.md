---
title: KOS Sim
deprecated: false
hidden: false
metadata:
  robots: index
---
![](https://files.readme.io/cf36bf6e3732121e6e5601a934b32fd119f8e7dab8ab98cc179dd7717e6ddaec-image.png)

<br />

`kos-sim` is a pure-simulation backend for the [K-Scale Operating System (KOS)](https://github.com/kscalelabs/kos), using the same gRPC interface. This lets you try out your KOS programs before deploying them onto a real robot. Once you're ready, you can run your code on the robot just by changing the client IP address.

## Installation

```bash
pip install kos-sim
```

## Getting Started

First, start the `kos-sim` backend:

```bash
kos-sim kbot-v1
```

Then, in a separate terminal, run one of the [repository examples](https://github.com/kscalelabs/kos-sim), such as:

```bash
python -m examples.kbot
```

You should see the simulated K-Bot move in response to the client commands.