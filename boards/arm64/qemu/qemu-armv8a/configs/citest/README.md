# `qemu-armv8a/configs/citest` Component (`boards/arm64/qemu/qemu-armv8a/configs/citest`)

## Overview
Board support component `configs/citest` for `qemu-armv8a` (`arm64/qemu`), containing 1 source/script file(s) (`run.sh`).

## Interface
- `[run.sh]` Shell script entry point `run.sh`

## Invariants
- `[run.sh:set]` Enforces shell execution mode (`set -e` / `set -o xtrace`)

## Side Effects
- `[run.sh]` Invokes host utilities (`ntfc`, `mkdir`, `mv`) to flash, debug, or test firmware

## Verification
- Run: `./tools/configure.sh qemu-armv8a:nsh && make`
