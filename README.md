# Zephyr™ Mechanical Keyboard (ZMK) Firmware

[![Discord](https://img.shields.io/discord/719497620560543766)](https://zmk.dev/community/discord/invite)
[![Build](https://github.com/zmkfirmware/zmk/workflows/Build/badge.svg)](https://github.com/zmkfirmware/zmk/actions)
[![Contributor Covenant](https://img.shields.io/badge/Contributor%20Covenant-v2.0%20adopted-ff69b4.svg)](CODE_OF_CONDUCT.md)

[ZMK Firmware](https://zmk.dev/) is an open source ([MIT](LICENSE)) keyboard firmware built on the [Zephyr™ Project](https://www.zephyrproject.org/) Real Time Operating System (RTOS). ZMK's goal is to provide a modern, wireless, and powerful firmware free of licensing issues.

Check out the website to learn more: https://zmk.dev/.

You can also come join our [ZMK Discord Server](https://zmk.dev/community/discord/invite).

To review features, check out the [feature overview](https://zmk.dev/docs/). ZMK is under active development, and new features are listed with the [enhancement label](https://github.com/zmkfirmware/zmk/issues?q=is%3Aissue+is%3Aopen+label%3Aenhancement) in GitHub. Please feel free to add 👍 to the issue description of any requests to upvote the feature.

# Introduction

The following is a fork from Zephyr™ Mechanical Keyboard (ZMK) Firmware taken at
commit `3f6841c95ff9a82658576828895ebcba1b0a5f86`.

All of my board specific configurations are maintained in their separate config files with their respective Nix devShell.

This repo does fetch them so I can test builds here too, however the intended way to build a board is to clone the corresponding config
repo.

## Building

For a general guide on how to build without using the GitHub actions please refer to [ZMK Building Flashing](https://zmk.dev/docs/development/local-toolchain/build-flash).

My current process involves:

```
west build -p -d build/left -b nice_nano_v2 -- -DSHIELD="kyria_rev3_left nice_view_adapter kyria_nice_view"
-DZMK_CONFIG="/home/matthew/ZYPHER/zmk-facehugger/config/kyria_zmk_config/config"
```

Keep in mind if building a new board or making changing like a new shield to include the pristine flag [(1)](https://zmk.dev/docs/development/local-toolchain/build-flash#pristine-building)

## Build Environment

My build environment is managed by NIX, please refer to my repo for the shell environment [ZEPHER ENV](https://github.com/MatthewWinnan/nixos-configs/tree/master/shells/zypher)

This is invoked using [direnv](https://direnv.net/) and including the following lines within the .envrc file:
`use flake /path/to/flakes#zypher`

Then use `direnv allow` to create the development environment within NIX.


