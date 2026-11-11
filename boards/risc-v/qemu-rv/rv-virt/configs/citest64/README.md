# `rv-virt/configs/citest64` Component (`boards/risc-v/qemu-rv/rv-virt/configs/citest64`)

## Overview
Board support component `configs/citest64` for `rv-virt` (`risc-v/qemu-rv`), containing 1 source/script file(s) (`run.sh`).

## Interface
- `[run.sh]` Shell script entry point `run.sh`

## Invariants
- `[run.sh:set]` Enforces shell execution mode (`set -e` / `set -o xtrace`)

## Side Effects
- `[run.sh]` Invokes host utilities (`ntfc`, `mkdir`, `mv`, `rm`) to flash, debug, or test firmware

## Verification
- Run: `./tools/configure.sh rv-virt:nsh && make`
