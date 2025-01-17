---
title: Recipe Title
description: Recipe Description
hidden: true
recipe:
  color: '#018FF4'
  icon: 🦉
---
```python Python
import time
import pykos

demo = "10.33.85.6"

alias = "demo"

ip_aliases = {
  "demo" : demo,
}

kos = pykos.KOS(ip=ip_aliases[alias])

ac = kos.actuator

all_ids = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16]

while True:
    print(ac.get_actuators_state(all_ids))
    time.sleep(0.1)
```

```json Response Example
{"success":true}
```

# TEST

<!-- python@ -->



# sdfadsfa

<!-- python@ -->



# sdfsdf

<!-- python@ -->

