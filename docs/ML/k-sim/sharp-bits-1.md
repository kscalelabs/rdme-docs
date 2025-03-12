---
title: Sharp bits
deprecated: false
hidden: false
metadata:
  robots: index
---
## MJCF definition

Changes to the MJCF can significantly impact the training speed. Here are the most important things to look at:

1. Boxes instead of even the most simplified meshes
2. Explicit contacts list
3. Addition of every new collision (even of a simple type) adds >10% slowness
4. Restrict maxhullvert parameter ([https://mujoco.readthedocs.io/en/stable/XMLreference.html#asset-mesh-maxhullvert](https://mujoco.readthedocs.io/en/stable/XMLreference.html#asset-mesh-maxhullvert))
5. Hfield behaves unreliably even with simpl geom types (see  [https://github.com/google-deepmind/mujoco/issues/1143](https://github.com/google-deepmind/mujoco/issues/1143))