---
title: Skillit Action Recorder
deprecated: false
hidden: false
metadata:
  robots: index
---
Import KOS into your project:

```python Python
import pykos
```

If you have a operational robot, you can now record your first actions.

To make it easier to get started with KOS skills, we've written a Python package to record and playback your robot's actions.

Just run

```Text bash
pip install skillit
```

and import anything you need!

```python Python
from skillit.play import FramePlayer
from skillit.record import SkillRecorder

# Mapping from names to joint ids. While the joint ids *need* to correspond
# to your actual actuator ids, the joint names can be whatever you want
joint_name_to_id = {
    "left_shoulder_yaw": 11,
    "left_shoulder_pitch": 12,
    "left_elbow_yaw": 13,
    "left_gripper": 14,
    "right_shoulder_yaw": 21,
    "right_shoulder_pitch": 22,
    "right_elbow_yaw": 23,
    "right_gripper": 24,
  
    "left_hip_yaw": 31,
    "left_hip_roll": 32,
    "left_hip_pitch": 33,
    "left_knee_pitch": 34,
    "left_ankle_pitch": 35,
  
    "right_hip_yaw": 41,
    "right_hip_roll": 42,
    "right_hip_pitch": 43,
    "right_knee_pitch": 44,
    "right_ankle_pitch": 45,
}

recorder = SkillRecorder(
    ip="192.168.42.1",
    joint_name_to_id=joint_name_to_id,
    frequency=20,  # Record at 20Hz
    countdown=3,  # 3 second countdown before recording
    skill_name="wave",  # Optional name for the skill
    )
```

Your skill will be saved as a json file that can also be played back with `skillit`

The repo and example scripts can be found [here](https://github.com/kscalelabs/skillit)