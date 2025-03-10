---
title: Mujoco Playground
excerpt: >-
  A simple and efficient library for training humanoid locomotion in MJX and
  MuJoCo.
deprecated: false
hidden: false
metadata:
  robots: index
---
## Getting Started

Clone our Mujoco Playground repository:

```bash
git clone https://github.com/kscalelabs/mujoco_playground.git
cd mujoco_playground
```

Install the package:

```text bash
pip install -e .
```

## Running ZBot experiments

You can train a standing policy within 20 min on RTX 4090

```bash
python playground/runner.py --env ZbotJoystickFlatTerrain
```

You can inpect the training performance through the reward plot or videos of evaluated policy.

If you have access to Google Colab you can try running the notebook:

```bash
ipython playground/.ipynb
```

## Evaluation (WIP)

You can inspect the training results through the output.mp4 file or running sim2sim evaluation through

```
python sim2sim.py --model_path 
```

<br />

> 🚧 Sim2Real pipeline WIP