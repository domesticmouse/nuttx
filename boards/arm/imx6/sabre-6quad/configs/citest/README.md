# `sabre-6quad/configs/citest` Component (`boards/arm/imx6/sabre-6quad/configs/citest`)

## Overview
Board support component `configs/citest` for `sabre-6quad` (`arm/imx6`), containing 1 source/script file(s) (`run.sh`).

## Interface
- `[run.sh]` Shell script entry point `run.sh`

## Invariants
- `[run.sh:set]` Enforces shell execution mode (`set -e` / `set -o xtrace`)

## Side Effects
- `[run.sh]` Invokes host utilities (`ntfc`, `mkdir`, `mv`, `rm`) to flash, debug, or test firmware

## Verification
- Run: `./tools/configure.sh sabre-6quad:nsh && make`
