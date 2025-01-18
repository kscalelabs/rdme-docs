---
title: Genesis
excerpt: A simple and efficient library for training humanoid locomotion in Genesis.
deprecated: false
hidden: false
metadata:
  robots: index
---
If you work on a Mac, you can install the package with the following command:

```shell Shell
micromamba create -n genesis python=3.12
micromamba activate genesis
```

If you work on a Linux machine, you can install the package with the following command:

```shell
conda create -n genesis python=3.12
conda activate genesis
```

Clone the repository:

```shell
git clone https://github.com/kscalelabs/genesis_playground.git
pip install genesis_playground
```

You can run the training and evaluation for Zeroth Bot with the following commands:

```shell
python zbot/zbot_train.py -e zbot-walking --num_envs 4096
```

On MacPro3 the training will take up to 30 min, you can evaluate some basic walking policy after first 5-10 minutes.

```
python zbot/zbot_eval.py -e zbot-walking --ckpt 100
```

<br />

> 🚧 Sim2Real pipeline WIP