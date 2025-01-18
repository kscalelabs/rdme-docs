---
title: Introduction to Skills Training
excerpt: >-
  See three different frameworks where you can train your humanoid to learn new
  skills.
deprecated: false
hidden: false
metadata:
  robots: index
next:
  description: >-
    See three different frameworks where you can train your humanoid to learn
    new skills.
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
## Introduction

Learning algorithms allow to train humanoids to perform different skills such as manipulation or locomotion. Below is an overview of general approaches to training machine learning models for humanoid robots with example applications. Typically you need a simulator, training framework and machine learning method to train end to end behaviors.

### Physics engines

Physics engines are software libraries designed to simulate physical systems in a virtual environment. They are crucial in a variety of fields such as video games, animation, robotics, and engineering simulations. These engines handle the mathematics involved in simulating physical processes like motion, collisions, and fluid dynamics

* PhysX is a physics engine by NVIDIA used primarily for video games and real-time simulations. It supports rigid body dynamics, cloth simulation, and particle effects, enhancing realism and interactivity in 3D environments.\
  MuJoCo
* MuJoCo (Multi-Joint dynamics with Contact) is a physics engine designed for research in robotics and biomechanics. It's known for its speed, accuracy, and ease of use, making it popular for simulating complex systems with robotics and articulated structures.
* Bullet  is a physics engine supporting real-time collision detection and multi-physics simulation for VR, games, visual effects, robotics, machine learning

<br />

### Training frameworks

We support three popular training frameworks

> 🚧

## Performance Analysis

Further analysis can be done on the outputs after doing the initial training.

## MJCF Visualizer

To visualize any MJCF file, you can run the following command:

```
python3 -m mujoco.viewer --mjcf \<path-to-mjcf-file>
```

The command above loads MuJoCo’s GUI, which allows you to simulate the model, manually specify joints, and save keyframes.