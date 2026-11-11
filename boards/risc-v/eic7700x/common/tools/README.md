# `common/tools` Component (`boards/risc-v/eic7700x/common/tools`)

## Overview
Board support component `tools` for `common` (`risc-v/eic7700x`), containing 1 source/script file(s) (`mkimage.sh`).

## Interface
- `[mkimage.sh]` Shell script entry point `mkimage.sh`

## Invariants
- `[mkimage.sh:set]` Enforces shell execution mode (`set -e` / `set -o xtrace`)
- `[mkimage.sh:exit]` Validates required environment variables, arguments, or files before execution

## Side Effects
- `[mkimage.sh]` Invokes host utilities (`genromfs`, `mkimage`, `rm`) to flash, debug, or test firmware

## Verification
- Run: `./tools/configure.sh sim:nsh && make`
