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

### Play Back Skills

python examples/play\_record\_example.py play --ip 10.33.11.238 --file ./skill\_video\_20250119\_021912.json

<br />

## Troubleshooting

* If servos lock: unplug servo power
* No response: check robot's power button
* For gRPC errors: restart KOS server