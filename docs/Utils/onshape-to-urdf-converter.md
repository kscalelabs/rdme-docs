---
title: KOL CAD to URDF Library
deprecated: false
hidden: false
metadata:
  robots: index
---
[https://github.com/kscalelabs/onshape](https://github.com/kscalelabs/onshape)

K-Scale OnShape Library `KOL` provides tooling for generating fully connected humanoid robot body files directly from an OnShape assembly.

Utilizing the OnShape API, `KOL` synthesizes model joint definitions, body properties, and layout into a standardized robotics file structure. The command line interface allows for downloading, checking, and implementing your robot directly into simulation environments.

# Getting Started

`KOL` is accessible through `pip`. If you encounter dependency issues, please see the below commands:

```bash
pip install kscale-onshape-library
pip install 'kscale-onshape-library @ git+https://github.com/kscalelabs/onshape.git@master'  //Install from Github
pip install 'kscale-onshape-library[all]' // Install all dependencies

```

## Set you API Key

With an OnShape account, you may request API keys at: [https://cad.onshape.com/appstore/dev-portal](https://cad.onshape.com/appstore/dev-portal)

These keys will need to be stored in your terminal environment (or else set in your *.bashrc*  *.zshrc* etc.):

```
export ONSHAPE_ACCESS_KEY=Your_Access_Key
export ONSHAPE_SECRET_KEY=Your_Secret_Key

```

<br />

## Minimal Run Example

```
kol run https://cad.onshape.com/documents/af093f8....
```

The most frequently used arguments with `kol run`  are:

* `-o "path/to/folderForRobot"` to specify location outputs of KOL is stored
  * Default will create a `robot` folder at your current working directory.
* `-f "configFilePath.yaml`

<br />

To also convert to a XML for MuJoCo, you need to specify a metadata.json file

<br />

Additional configuration options are defined in the config file \[[https://github.com/kscalelabs/onshape/blob/master/kol/onshape/config.py\](](https://github.com/kscalelabs/onshape/blob/master/kol/onshape/config.py]\()[https://github.com/kscalelabs/onshape/blob/master/kol/onshape/config.py](https://github.com/kscalelabs/onshape/blob/master/kol/onshape/config.py))

<br />

## General Commands

* `download`: Downloads the model and establishes an initial URDF.

```
kol download <document-url> (--output-dir <output-directory>)
```

* `postprocesss`: Processes the provided URDF for use.

```
kol postprocess <urdf-path>
```

* `run`: Combined download and postprocessing. Similar argument options to `download`.
* `pybullet`: Simulates the provided urdf in a basic pybullet environment.

```
kol pybullet <urdf-path> [options]
```

<br />

## Config File Reference

**Ignore Welding Joints**

By default, fixture joints on the same body gets combined into one body. To avoid this you can set the following params:

```yaml
ignore_merging_fixed_joints:
  - "imu_link"
```

or

```yaml
merge_fixed_joints: false
```

<br />

**Examples**

<Accordion title="Full Example with Robot" icon="fa-info-circle">
  ```yaml
  default_revolute_joint_effort: 17
  default_revolute_joint_velocity: 360
  suffix_to_joint_effort:
    "_00": 14
    "_02": 17
    "_03": 60
    "_04": 120
  suffix_to_joint_velocity:
    "_00": 12.566
    "_02": 12.566
    "_03": 6.283
    "_04": 6.283
  convex_collision_meshes: true

  ignore_merging_fixed_joints:
    - "imu_link"

  rotate_joints:
    imu_link: [-90.0, 0.0, 0.0]

  max_mesh_triangles: 10000
  max_convex_collision_mesh_triangles: 100

  exclude_collision_meshes:
    # Shoulder yoke stops.
    - "YOKE_STOP_INNER"
    - "YOKE_STOP_INNER_2"
    # Hip yoke stops.
    - "KB_D_102L_L_Hip_Yoke_Drive"
    - "KB_D_102R_R_Hip_Yoke_Drive"
    # Upper arms
    - "L_Bicep_Lower_Drive"
    - "R_Bicep_Lower_Drive"
    # Forearms
    - "L_Forearm_Upper_Drive"
    - "R_Forearm_Upper_Structural"
    # Knee
    - "KB_D_301R_R_Femur_Lower_Drive"
    - "KB_D_301L_L_Femur_Lower_Drive"
    # IMU
    - "imu"

  shrink_collision_meshes:
    # Leg roll
    "RS03_4": 0.8
    "RS03_3": 0.8
    # Ankle
    "KB_D_401R_R_Shin_Drive": 0.85
    "KB_D_402L_L_Shin_Idle": 0.85
    # Wrist
    "KB_C_501X_Bayonet_Adapter_Hard_Stop": 0.8
    "KB_C_501X_Bayonet_Adapter_Hard_Stop_2": 0.8
    # Base
    "KB_B_102B_TORSO_BOTTOM": 0.8

  move_collision_meshes:
    "R_Bicep_Lower_Drive": [0.0, 0.0, -0.01]
    "L_Bicep_Lower_Drive": [0.0, 0.0, -0.01]

  joint_separation_distance: 0.001

  base_rpy:
    - 0
    - 0
    - 4.7123889803 # So that x is forward in mujoco

  flip_joints:
    - "left_knee_04"
    - "left_shoulder_roll_03"
    - "right_shoulder_roll_03"
    - "left_hip_roll_03"
    - "right_hip_roll_03"
    - "left_ankle_02"

  mjcf_metadata:
    joint_params:
      - name: "motor_00"
        armature: 0.0005
        frictionloss: 0.1
        actuatorfrc: 14
        suffixes: ["_00"]
      - name: "motor_02"
        armature: 0.002
        frictionloss: 0.1
        actuatorfrc: 17
        suffixes: ["_02"]
      - name: "motor_03"
        armature: 0.005
        frictionloss: 0.3
        actuatorfrc: 60
        suffixes: ["_03"]
      - name: "motor_04"
        armature: 0.007
        frictionloss: 0.1
        actuatorfrc: 120
        suffixes: ["_04"]

    # imus:
    #   - body_name: "imu"
    #     acc_noise: 0.01
    #     gyro_noise: 0.01
    #     mag_noise: 0.05
  # This is for debugging purposes.
  # use_collision_meshes_as_visual_meshes: true
  ```
</Accordion>

<br />

# CAD Considerations

`KOL` currently only supports  `Fixture` mates and `Revolute` joints.

* Set joint limits on all `Revolute` joints. Pay attention to orientation of the axes and the 0-position. OnShape provides a dropdown action "reset" on all mates to return to 0-position.
* Ensure that there are no redundant mates in your assembly, as they will interfere with generating a sensible graph structure for the URDF.

<br />

To identify left and right orientation of bodies, `KOL` requires the syntax `L_<item>` and `R_<item>` for the `Revolute` joints.

* As in `L_Thigh_Yaw` or `R_ElbowPitch`

<br />

`KOL` does not ensure functionality of OnShape assembly configurations.

# Additional Resources

## OnShape API

* [OnShape API Explorer Glassworks](https://cad.onshape.com/glassworks/explorer/)
* [OnShape API Documentation](https://onshape-public.github.io/docs/api-intro/)

<br />

## Other Tools

* [Rhoban's Onshape-to-Robot Github](https://github.com/Rhoban/onshape-to-robot)