---
title: Start building with KOS
excerpt: Learn to develop and control K-Scale robots with our open-source software.
deprecated: false
hidden: false
metadata:
  robots: index
next:
  pages:
    - slug: set-up-your-environment
      title: Set up your environment
      type: basic
    - slug: build-and-test-skills
      title: Building and testing skills
      type: basic
---
## Introduction

`pykos` is a Python client for the K-Scale Operating System (KOS), allowing you to interact with various services provided by KOS, such as controlling actuators, accessing IMU data, managing processes, and more.

## Installation

To install `pykos`, you can use pip:

```shell
pip install pykos
```

## Getting Started

First, import the `pykos` module and create an instance of the KOS client:

```python
from pykos import KOS

# Connect to KOS running on localhost at port 50051
client = KOS(ip='localhost', port=50051)
```

<br />

## Services

The KOS client provides several services, each accessible via the client object. Below are the services and examples of how to use them.