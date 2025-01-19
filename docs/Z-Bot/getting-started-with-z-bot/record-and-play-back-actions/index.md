---
title: Record and Play Back Actions
deprecated: false
hidden: false
metadata:
  robots: index
---
# Robot Skill Recording Guide

<br />

## Connection

* If connected via USB cable, use IP: 192.168.42.1
* If connected wirelessly, use IP: 10.33.11.238
* SSH into robot: ssh root@\[IP\_ADDRESS]

<br />

# Server Management

### Stop server

killall kos

### Start server with logging

/usr/local/bin/kos --log --log-level trace

### Test Joints

python examples/move\_all\_joints\_a\_little.py

[https://github.com/kscalelabs/skillet/blob/master/skillet/examples/move\_all\_joints\_a\_little.py](https://github.com/kscalelabs/skillet/blob/master/skillet/examples/move_all_joints_a_little.py)

<br />

## Record Skills

### Replace \[SKILL\_NAME] with your chosen name (e.g., wave, dance, etc)

python examples/play\_record\_example.py record --ip 10.33.11.238 --skill-name \[SKILL\_NAME]

### After recording, the file will be saved as skill\_\[SKILL\_NAME]\_\[TIMESTAMP].json

### Example: skill\_wave\_20250119\_021912.json

## Play Back Skills

### Use the full filename that was created during recording

python examples/play\_record\_example.py play --ip 10.33.11.238 --file ./skill\_\[SKILL\_NAME]\_\[TIMESTAMP].json

[https://github.com/kscalelabs/skillit/blob/master/examples/play\_record\_example.py](https://github.com/kscalelabs/skillit/blob/master/examples/play_record_example.py)

<br />

## Troubleshooting

* If servos lock: unplug servo power
* No response: check robot's power button
* For gRPC errors: restart KOS server