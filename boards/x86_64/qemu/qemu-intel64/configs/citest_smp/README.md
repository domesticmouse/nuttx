# `qemu-intel64/configs/citest_smp` Component (`boards/x86_64/qemu/qemu-intel64/configs/citest_smp`)

## Overview
Board support component `configs/citest_smp` for `qemu-intel64` (`x86_64/qemu`), containing 1 source/script file(s) (`run.sh`).

## Interface
- `[run.sh]` Shell script entry point `run.sh`

## Invariants
- `[run.sh:set]` Enforces shell execution mode (`set -e` / `set -o xtrace`)

## Side Effects
- `[run.sh]` Invokes host utilities (`ntfc`, `mkdir`, `mv`, `rm`) to flash, debug, or test firmware

## Verification
- Run: `./tools/configure.sh qemu-intel64:nsh && make`
