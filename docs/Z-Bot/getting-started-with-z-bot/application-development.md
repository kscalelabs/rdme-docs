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

```python
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

## Getting Started

Use the starter code in the [skillet](https://github.com/kscalelabs/skillet/tree/master) repo to test your actuators.

You will need python 3.11 to run this code.

### Installation

<br />

```bash bash

# clone this repo
# in the root folder of the repo do 
pip install -e .

```

### Usage

#### Run move all actuators

This will move each joint 5 degrees and print any that failed.

```bash bash
# from the root folder of the repo, run
python skillet/examples/move_all_joints_a_little.py
```