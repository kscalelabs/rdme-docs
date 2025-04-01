---
title: Zeroth Bot
excerpt: >-
  The world's most affordable and open-source humanoid robot, powered by
  end-to-end models.
deprecated: false
hidden: false
metadata:
  robots: index
---
Zeroth Bot is an open-source humanoid robot development platform designed for developers and researchers, made for advanced ML and software applications development.

## Joint Motors

<Image align="center" src="https://files.readme.io/55ea9222399e998e74877705053dc1ecf1643204553f4006d3d1799544d2b3e4-zbot.png" />

## Robot Composition

The Zeroth Bot consists of head, torso, arms, and legs, with total 16 DoFs, allowing for flexible movement and control:

* Each arm has 3 DoF + 1 DoF Gripper
* Each leg has 6 DoF
* Battery, IMU, camera, microphone, and speaker are installed in the torso

## Robot Functions (coming soon)

* Omnidirectional walking
  * Supports forward, backward, and lateral walking
  * Supports rotation and complex walking
* Disturbance Resistance While Walking
  * Can walk on uneven surfaces
  * Can withstand certain impact disturbances while walking
* Predefined Actions
  * Waving
* Safety Protection
  * Automatically enters damping model in uncontrolled states to prevent damage
  * Hard emergency stop
  * Soft emergency stop