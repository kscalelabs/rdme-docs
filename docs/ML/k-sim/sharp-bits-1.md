---
title: Sharp bits
deprecated: false
hidden: false
metadata:
  robots: index
---
[https://github.com/google-deepmind/mujoco/issues/1143##](https://github.com/google-deepmind/mujoco/issues/1143##) MJCF definition

Changes to the MJCF can significantly impact the training speed. Here are the most important things to look at:

1. Boxes instead of even the most simplified meshes
2. Explicit contacts list
3. Addition of every new collision (even of a simple type) adds >10% slowness
4. Restrict [maxhullvert](https://mujoco.readthedocs.io/en/stable/XMLreference.html#asset-mesh-maxhullvert) parameter below 64 or less.
5. Hfield behaves [unreliably](https://github.com/google-deepmind/mujoco/issues/1143) even with simple geom types.