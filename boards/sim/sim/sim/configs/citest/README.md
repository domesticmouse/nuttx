# `sim/configs/citest` Component (`boards/sim/sim/sim/configs/citest`)

## Overview
Board support component `configs/citest` for `sim` (`sim/sim`), containing 1 source/script file(s) (`run.sh`).

## Interface
- `[run.sh]` Shell script entry point `run.sh`

## Invariants
- `[run.sh:set]` Enforces shell execution mode (`set -e` / `set -o xtrace`)

## Side Effects
- `[run.sh]` Invokes host utilities (`ntfc`, `mkdir`, `mv`, `rm`) to flash, debug, or test firmware

## Verification
- Run: `./tools/configure.sh sim:nsh && make`
