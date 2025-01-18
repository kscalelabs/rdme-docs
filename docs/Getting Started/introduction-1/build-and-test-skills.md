---
title: Building and testing skills
deprecated: false
hidden: false
metadata:
  robots: index
---
Import KOS into your project:

```python Python
import pykos
```

If you have a operational robot, you can now program your first skill.

<TutorialTile emoji="🦉" slug="make-your-robot-wave" title="Make your Robot wave" />

To make it easier to get started with KOS skills, we've written a Python package to record and playback your robot's actions.

Just run

```Text bash
pip install skillet
```

and import anything you need!

```Text Python
from skillit.play import FramePlayer
from skillit.record import SkillRecorder

# Mapping from names to joint ids. While the joint ids *need* to correspond
# to your actual actuator ids, the joint names can be whatever you want
joint_name_to_id = {
    "right_ankle_pitch": 1,
    "right_knee_pitch": 2,
    "right_hip_pitch": 3,
    "right_hip_roll": 4,
    "right_hip_yaw": 5,
    "left_ankle_pitch": 6,
    "left_knee_pitch": 7,
    "left_hip_pitch": 8,
    "left_hip_roll": 9,
    "left_hip_yaw": 10,
    "right_elbow": 11,
    "right_shoulder_pitch": 12,
    "right_shoulder_roll": 13,
    "left_elbow": 16,
    "left_shoulder_pitch": 15,
    "left_shoulder_roll": 14,
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