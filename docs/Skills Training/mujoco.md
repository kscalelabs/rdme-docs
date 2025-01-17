---
title: Mujoco Playground
excerpt: Getting started with MuJoCo Playground physics simulation with K-Scale Bots.
deprecated: false
hidden: false
metadata:
  robots: index
---
## Getting Started

Clone this repository

```bash
git clone https://github.com/kscalelabs/mujoco_playground.git
pip install mujoco_playground
```

2. Follow standard installation instructions for [Mujoco Playground](https://github.com/google-deepmind/mujoco_playground)

## Running ZBot experiments

Run a small training with visualization with the following command:

```bash
python run_local_training.py
```

or through notebook:

```bash
ipython run_local_training.ipynb
```

## Evaluation

You can inspect the training results through the output.mp4 file or running sim2sim evaluation through

```
python sim2sim.py --model_path 
```