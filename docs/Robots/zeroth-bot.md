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

* Each arm has 3 DoF
* Each leg has 5 DoF
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

## Robot Specifications

| Type                   | Specification Parameters       | Description                                              |
| ---------------------- | ------------------------------ | -------------------------------------------------------- |
| Basic Parameters       | Height (when standing upright) | 48cm                                                     |
|                        | Weight                         | 3.6kg                                                    |
| DoFs                   | Total DoFs                     | 16                                                       |
|                        | Single Leg DoFs                | 5                                                        |
|                        | Single Arm DoFs                | 3 (expandable)                                           |
| Operational Parameters | Walking Speed                  |                                                          |
|                        | Turning Speed                  |                                                          |
| Battery Parameters     | Battery Life                   | 20 Minutes                                               |
|                        | Charging Time                  | ≤ 2h                                                     |
|                        | Cycle Life                     |                                                          |
| Computing Platform     | CPU                            | RISC-V 0.5 Tops (Extensible to 26 TOPS with AI Backpack) |
| Actuators              | Torque                         | 30kg.cm                                                  |
|                        | Speed                          | 60RPM                                                    |
| Sensors                | Camera                         | 1080p Camera                                             |
|                        | Microphone                     | Electret microphone                                      |
|                        | Speaker                        | 3W Speaker                                               |
|                        | IMU                            | 6-axis sensor                                            |
| Safety Function        | Robot Emergency Stop           | 1                                                        |
|                        | Auditory Alerts                | Low Battery Alert, Joint Overheat Alert                  |
| Communication Methods  | Wireless Connections           | WIFI 6                                                   |
|                        | GPRC                           |                                                          |