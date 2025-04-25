---
title: Z-Bot
excerpt: The world's most affordable and open-source humanoid robot.
deprecated: false
hidden: false
metadata:
  robots: index
---
Zeroth Bot, or Z-Bot, is an open-source humanoid robot development platform designed for developers and researchers, made for advanced ML and software applications development.

<Image align="center" border={false} src="https://files.readme.io/c3113928dcaf24c38d8528dd6f25762e5e36d744773c3e7c073f5645803030a0-image.png" width="500em" />

<Cards columns={3}>
  <Card title="Z-Bot" href="https://www.zerothbot.com/" icon="fa-globe" target="_blank">
    The Z-Bot website
  </Card>

  <Card title="K-OS" href="https://github.com/kscalelabs/kos-zbot" icon="fa-user">
    K-OS backend for Z-Bot
  </Card>

  <Card title="K-Sim" href="https://github.com/kscalelabs/ksim-zbot" icon="fa-star">
    K-Sim policy training and deployment for Z-Bot
  </Card>
</Cards>

## Motor ID Mappings

<Image align="center" src="https://files.readme.io/0fd0e4a199ec07382b7cbcfcd0c623d4e7ec178c650898664934d1fed12bc624-Zeroth_Bot_Motor_Join_ID_Diagram.png" />

## Robot Composition

The Zeroth Bot consists of head, torso, arms, and legs, with total 16 DoFs, allowing for flexible movement and control:

* Each arm has 3 DoF + 1 DoF Gripper
* Each leg has 6 DoF
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