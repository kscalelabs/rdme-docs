---
title: Robot Overview
deprecated: false
hidden: false
metadata:
  robots: index
---
Zeroth Bot is an open-source humanoid robot development platform designed for developers and researchers, made for advanced ML and software applications development.

## Robot Composition

The Zeroth Bot consists of head, torso, arms, and legs, with total 16 DoFs, allowing for flexible movement and control:

* Each arm has 3 DoF
* Each leg has 5 DoF
* Battery, IMU, camera, microphone, and speaker are installed in the torso

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
|                        |                                |                                                          |

## Joint Motors

![](https://files.readme.io/b72839a04316c7ea135c56706bd7497bf465fc5fb6f230aa883b063e821a05e1-image.png)

<br />

### Joint ID and Limits

| Joint ID | Joint Name | Max Limit (Deg) | Min Limit (Deg) |
| -------- | ---------- | --------------- | --------------- |
| 11       |            |                 |                 |
| 12       |            |                 |                 |
| 13       |            |                 |                 |
| 14       |            |                 |                 |
| 21       |            |                 |                 |
| 22       |            |                 |                 |
| 23       |            |                 |                 |
| 24       |            |                 |                 |
| 31       |            |                 |                 |
| 32       |            |                 |                 |
| 33       |            |                 |                 |
| 34       |            |                 |                 |
| 35       |            |                 |                 |
| 41       |            |                 |                 |
| 42       |            |                 |                 |
| 43       |            |                 |                 |
| 44       |            |                 |                 |
| 45       |            |                 |                 |

### Coordinate System

The joint coordinate system with all joints at zero position is shown in the diagram below.

\[robot in zero position]

## Controller

|   |   |
| - | - |
|   |   |
|   |   |

Computing Power: RISC-V Dual Core 0.5TOPS NPU (Extensible to 26 TOPS with AI Backpack)

Network: WI-FI6/BT5 onboard

Video: 1080p camera

Audio: Speaker, Microphone