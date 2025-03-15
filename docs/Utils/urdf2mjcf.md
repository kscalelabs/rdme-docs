---
title: URDF to Mujoco Converter
excerpt: Utility for converting from URDF format to Mujoco format
deprecated: false
hidden: false
metadata:
  robots: index
---
`urdf2mjcf` is a tool for converting URDF models to Mujoco XML.

Here is an example, with the input URDF on the right and the output MJCF on the left:

<Image align="center" src="https://files.readme.io/88353b2712e56119be059d02b21b61ef0f220713053b23eeab57770691a287d2-Screenshot_2025-01-29_at_15.29.15.png" />

## Installation

You can install the package using `pip`:

```
pip install urdf2mjcf
```

## Usage

### Command Line

To run the conversion script from the command line, use:

```
urdf2mjcf path/to/your/robot.urdf
```

This will save the MJCF file in the same directory as the URDF file.

To see all the options, use:

```
urdf2mjcf -h
```

As of `urdf2mjcf==0.0.4`, the options are:

```
usage: urdf2mjcf [-h] [--no-collision-mesh] [--output OUTPUT] [--copy-meshes]
                 [--camera-distance CAMERA_DISTANCE]
                 [--camera-height-offset CAMERA_HEIGHT_OFFSET]
                 [--no-frc-limit] [--default-position DEFAULT_POSITION]
                 urdf_path

Convert a URDF file to an MJCF file.

positional arguments:
  urdf_path             The path to the URDF file.

options:
  -h, --help            show this help message and exit
  --no-collision-mesh   Do not include collision meshes.
  --output OUTPUT       The path to the output MJCF file.
  --copy-meshes         Copy mesh files to the output MJCF directory.
  --camera-distance CAMERA_DISTANCE
                        Camera distance from the robot.
  --camera-height-offset CAMERA_HEIGHT_OFFSET
                        Camera height offset.
  --no-frc-limit        Do not include force limit for the actuators.
  --default-position DEFAULT_POSITION
                        Default position for the robot.
```

### Python

To run the conversion script from Python, use:

```
from urdf2mjcf import run

run(
    urdf_path="path/to/your/robot.urdf",
    mjcf_path="path/to/save/robot.mjcf",
    copy_meshes=True,
)
```