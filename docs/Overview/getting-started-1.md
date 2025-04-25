---
title: Getting Started
excerpt: How to contribute to making robots more useful
deprecated: false
hidden: false
metadata:
  robots: index
---
At K-Scale, we believe in developing in the open, since it is the lowest-friction way for us to make progress towards our mission of building a billion humanoid robots. The problem is that this usually means you need to have a robot before you can start working on it. To solve this problem, we've built a set of tools to make it easy to get started before you have your own robot, letting you easily run your code on our robot instead.

## Dependencies

You can get started with just your laptop, but we suggest using a GPU for training your own models. We usually use 4090's but this should work for other GPUs as well.

## Getting Started

1. Create a new environment using Python 3.11 or later. We recommend using [uv](https://docs.astral.sh/uv/)
2. Install `ksim`

```python
pip install ksim
```

## Training a Policy

To train a policy