---
title: Introduction to Skills Training
deprecated: false
hidden: false
metadata:
  robots: index
next:
  pages:
    - slug: isaac-lab
      title: Isaac Lab
      type: basic
    - slug: genesis
      title: Genesis
      type: basic
    - slug: mujoco
      title: Mujoco Playground
      type: basic
---
What is simulator,

how to train standing, walking

How to try to deploy

<br />

## MJCF Visualizer

To visualize any MJCF file, you can run the following command:

```
python3 -m mujoco.viewer --mjcf \<path-to-mjcf-file>
```

The command above loads MuJoCo’s GUI, which allows you to simulate the model, manually specify joints, and save keyframes.

## Performance Analysis

Further analysis can be done on the outputs after doing the initial training.

You will be prompted to make an account with Weights and Biases WandB when first performing train.py. Basic statistics on the ML training process will be provided online afterwards.

For information on the kinematics and controls of the model, it is possible to generate an HDF5 dataset when running play.py. This currently includes:

x, y, and yaw commands\
Joint positiions and velocities
Joint ‘actions’, relating to the input torque
Among others; see sim/sim/play.py for the exact outputs.