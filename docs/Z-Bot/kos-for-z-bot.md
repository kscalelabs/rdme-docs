---
title: KOS for Z-Bot
deprecated: false
hidden: false
metadata:
  robots: index
---
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

![](https://files.readme.io/26479e0947ff034bc343193914363ab40ea186000ab84661ed9676b21f5e5565-image.png)

Buildroot: [https://github.com/zeroth-robotics/buildroot](https://github.com/zeroth-robotics/buildroot)