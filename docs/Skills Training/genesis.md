---
title: Genesis
deprecated: false
hidden: false
metadata:
  robots: index
---
Clone the repository:

```bash
git clone https://github.com/kscalelabs/genesis_playground.git
pip install genesis_playground

```

If you work on a Mac, you can install the package with the following command:

```bash
micromamba create -n genesis python=3.12
micromamba activate genesis
pip install genesis-world
git clone https://github.com/leggedrobotics/rsl_rl
cd rsl_rl && git checkout v1.0.2 && pip install -e .
pip install tensorboard
```

If you work on a Linux machine, you can install the package with the following command:

```bash
conda create -n genesis python=3.12
conda activate genesis
pip install genesis-world
git clone https://github.com/leggedrobotics/rsl_rl
cd rsl_rl && git checkout v1.0.2 && pip install -e .
pip install tensorboard
```

You can run the training and evaluation for Zeroth Bot with the following commands:

```bash
python zbot/zbot_train.py -e zbot-walking --num_envs 4096
python zbot/zbot_eval.py -e zbot-walking --ckpt 100
```

On MacPro3 the training will take up to 30 min, you can evaluate some basic walking policy after first 5-10 minutes.