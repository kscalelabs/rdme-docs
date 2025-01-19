---
title: Record and Play Back Actions
deprecated: false
hidden: false
metadata:
  robots: index
---
How to record and play back

make sure your robot is connected via wifi

Then ssh into robot so you can start and restart the server (this is important)

Whenever getting a grpc error or if your actuators are locked up run

killall kos (to kill the client server)

Now run this /usr/local/bin/kos --log --log-level trace to start the server again with logging

Now run python examples/move\_all\_joints\_a\_little.py to check all your joints

(If at any point you get really stuck, unplug power from your servos)

Also note that the button cuts power to the servos so if your servos are saying they are running but are not, try pushing the button

cd kscale/skillet

python examples/play\_record\_example.py record  --ip 10.33.11.238 --skill-name video to start recording

play back like this python examples/play\_record\_example.py play --ip 10.33.11.238 --file ./skill\_video\_20250119\_021912.json