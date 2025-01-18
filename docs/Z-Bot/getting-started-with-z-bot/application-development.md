---
title: Programming Z-Bot
excerpt: Anybody that can write Python can program this robot
deprecated: false
hidden: false
metadata:
  robots: index
---
[K-Scale OS](https://kscale.readme.io/update/docs/kos#/)

Use this convention for assigning names to the actuator ids.

```Text python
actuator_name_to_id = {
    'left_shoulder_yaw' : 11,
    'left_shoulder_pitch' : 12,
    'left_elbow_yaw' : 13,
    'left_gripper' : 14,
    'right_shoulder_yaw' : 21,
    'right_shoulder_pitch' : 22,
    'right_elbow_yaw' : 23,
    'right_gripper' : 24,
    'left_hip_yaw' : 31,
    'left_hip_roll' : 32,
    'left_hip_pitch' : 33,
    'left_knee_pitch' : 34,
    'left_ankle_pitch' : 35,
    'right_hip_yaw' : 41,
    'right_hip_roll' : 42,
    'right_hip_pitch' : 43,
    'right_knee_pitch' : 44,
    'right_ankle_pitch' : 45,
}
```