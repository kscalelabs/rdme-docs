---
title: Urdf to Mujoco Converter
deprecated: false
hidden: false
metadata:
  robots: index
---
# URDF to Mujoco Converter

`urdf2mjcf` is a tool for converting URDF models to Mujoco XML.

Here is an example, with the input URDF on the right and the output MJCF on the left:

\<Image\
src=\{urdf2mjcf\_example}
alt="URDF to MJCF"
width="100%"
className="mx-auto"
style=\{\{ marginTop: '1em', marginBottom: '1em' }}
/>

## Installation

<br />

You can install the package using `pip`:

<br />

```
```

<br />

## Usage

<br />

<br />

### Command Line

<br />

To run the conversion script from the command line, use:

<br />

```
```

<br />

This will save the MJCF file in the same directory as the URDF file.

<br />

To see all the options, use:

<br />

```
```

<br />

As of `urdf2mjcf==0.0.4`, the options are:\`\`\`bash\
usage: urdf2mjcf \[-h] \[--no-collision-mesh] \[--output OUTPUT] \[--copy-meshes]
\[--camera-distance CAMERA\_DISTANCE]
\[--camera-height-offset CAMERA\_HEIGHT\_OFFSET]
\[--no-frc-limit] \[--default-position DEFAULT\_POSITION]
urdf\_path

````

<br />

Convert a URDF file to an MJCF file.

<br />

positional arguments:\
urdf\_path             The path to the URDF file.

<br />

options:\
-h, --help            show this help message and exit
\--no-collision-mesh   Do not include collision meshes.
\--output OUTPUT       The path to the output MJCF file.
\--copy-meshes         Copy mesh files to the output MJCF directory.
\--camera-distance CAMERA\_DISTANCE
Camera distance from the robot.
\--camera-height-offset CAMERA\_HEIGHT\_OFFSET
Camera height offset.
\--no-frc-limit        Do not include force limit for the actuators.
\--default-position DEFAULT\_POSITION
Default position for the robot.```
````

<br />

### Python

<br />

To run the conversion script from Python, use:

<br />

```
```

<br />

run(\
urdf\_path="path/to/your/robot.urdf",
mjcf\_path="path/to/save/robot.mjcf",
copy\_meshes=True,
)\`\`\`

```
```