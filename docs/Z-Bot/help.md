---
title: FAQ
deprecated: false
hidden: false
metadata:
  robots: index
---
Main repo: [https://github.com/zeroth-robotics/zeroth-bot](https://github.com/zeroth-robotics/zeroth-bot)

Corresponding gitlab: [https://gitlab.kscale.ai/zeroth-robotics/OpenLCH](https://gitlab.kscale.ai/zeroth-robotics/OpenLCH)

# KOS for Z-Bot

## I want to work on KOS for Z-Bot but don’t know where it is

right here → [https://github.com/zeroth-robotics/zeroth-bot/tree/main/runtime/kos\_platform](https://github.com/zeroth-robotics/zeroth-bot/tree/main/runtime/kos_platform)

## Okay, how do I build it?

Simple! Just run

```bash
gitlab-ci-local --stage build-runtime
```

Make sure your docker is on

## Where do I get gitlab-ci-local?

idk try running

```bash
brew install gitlab-ci-local
```

## Cool, what does this do?

Runs jobs specified in [https://github.com/zeroth-robotics/zeroth-bot/blob/main/.gitlab-ci.yml](https://github.com/zeroth-robotics/zeroth-bot/blob/main/.gitlab-ci.yml)

E.g. define your stages like:

```bash
stages:
  - build-toolchain
  - build-components
  - build-runtime
  
 build-kos:
  <<: *runner
  stage: build-runtime # <------- !!!!!
  needs:
    - build-cviwrapper
    - build-servo
  image: $TOOLCHAIN_IMAGE:latest
  variables:
    CC_riscv64gc_unknown_linux_musl: "/sdk/host/bin/riscv64-buildroot-linux-musl-gcc.br_real"
  script:
    - git clone https://github.com/kscalelabs/kos.git --depth 1 --branch zbot-feetechv2
    - cd kos
    - rm -rf platforms/zeroth-01; ln -s $PWD/../runtime/kos_platform platforms/zeroth-01
    - source /root/.cargo/env
    - cargo +nightly build --target riscv64gc-unknown-linux-musl -F kos-zeroth-01 -Zbuild-std --release

  artifacts:
    paths:
      - kos/target/riscv64gc-unknown-linux-musl/release/kos
    expire_in: 1 week
  rules:
    - if: $CI_PIPELINE_SOURCE == "push"
      changes:
        - runtime/kos_platform/**/*
        - .gitlab-ci.yml
```

And build-kos is run when you specify build-runtime

## Cool, now where do I find my kos?

It’ll be specified in someplace like

```bash
  artifacts:
    paths:
      - kos/target/riscv64gc-unknown-linux-musl/release/kos # <----- !!!!!!
    expire_in: 1 week
```

## Okay… but where is that on my machine?

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/90bfd7cd-abb5-4278-98f7-34932f644926/a0d3697b-a48d-4379-97b2-77062cd8b940/image.png)

Buildroot: [https://github.com/zeroth-robotics/buildroot](https://github.com/zeroth-robotics/buildroot)

# Flashing Z-Bot

## Basics

### Finding your image

Find the release you want to use: [https://github.com/zeroth-robotics/buildroot/releases](https://github.com/zeroth-robotics/buildroot/releases)

Navigate to the corresponding Gitlab job here (by commit or tag or branch or however you want): [https://gitlab.kscale.ai/zeroth-robotics/OpenLCH-buildroot/-/artifacts](https://gitlab.kscale.ai/zeroth-robotics/OpenLCH-buildroot/-/artifacts)

![](https://files.readme.io/6b5dd1909b146dd853e01f753824024facda14d52c1e6bbaf560d8cf5319a3bc-image.png)

<br />

### Download the artifacts

![](https://files.readme.io/ef80461cce6168f67ced7212f499420c84658482f299a2b143a0ecc4d0a7eb18-image.png)

<br />

### Extract your .img file

![](https://files.readme.io/22bbb1edff4eb30ff0cf84ae49ae811b6a6bbc899717c6321927d33ba2107aed-image.png)

<br />

### Then flash the img onto a micro-SD card using something like BalenaEtcher

![](https://files.readme.io/d91454a31eb1bbbca675339ee48cfcf739ba3e0f79e26b8ca02cef8e80501066-image.png)

<br />

![](https://files.readme.io/57b9cabd7db28e198fec22c250b436bf790d82b089b88184c0945aed0055c403-image.png)

<br />

### And you’re done!

## Optionally

Once you’ve ssh’d into your MilkV over USB (ip = 192.168.42.1)

```bash
ssh root@192.168.42.1

# Copy wpa_supplicant file
cp /etc/wpa_supplicant.conf /boot/

# Add your network
vim /boot/wpa_supplicant.conf
```