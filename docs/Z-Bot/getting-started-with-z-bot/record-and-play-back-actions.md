---
title: Record and Play Back Actions
deprecated: false
hidden: false
metadata:
  robots: index
---
# Robot Skill Recording Guide

## Setup

1. Connect robot to WiFi
2. SSH into robot so you can start/restart the server
3. Navigate to the project: cd kscale/skillit

## Server Management

# Stop server

killall kos

# Start server with logging

/usr/local/bin/kos --log --log-level trace

## Test Joints

python examples/move\_all\_joints\_a\_little.py

## Record Skills

python examples/play\_record\_example.py record --ip 10.33.11.238 --skill-name video

## Play Back Skills

python examples/play\_record\_example.py play --ip 10.33.11.238 --file ./skill\_video\_20250119\_021912.json

## Troubleshooting

* If servos lock: unplug servo power
* No response: check robot's power button
* For gRPC errors: restart KOS server