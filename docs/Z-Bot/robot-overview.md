---
title: Robot Overview
deprecated: false
hidden: false
metadata:
  robots: index
---
Zeroth Bot is an open-source humanoid robot development platform designed for developers and researchers, made for advanced ML and software applications development.

<br />

## Robot Composition

The Zeroth Bot consists of head, torso, arms, and legs, with total 16 DoFs, allowing for flexible movement and control:

* Each arm has 3 DoF
* Each leg has 5 DoF
* Battery, IMU, camera, microphone, and speaker are installed in the torso

<br />

## Robot Functions

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