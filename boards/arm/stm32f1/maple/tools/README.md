# `maple/tools` Component (`boards/arm/stm32f1/maple/tools`)

## Overview
Board support component `tools` for `maple` (`arm/stm32f1`), containing 2 source/script file(s) (`dfu.sh, env.sh`).

## Interface
- `[dfu.sh]` Shell script entry point `dfu.sh`
- `[env.sh]` Shell script entry point `env.sh`

## Invariants
- None

## Side Effects
- `[dfu.sh]` Invokes host utilities (`dfu-util`) to flash, debug, or test firmware
- `[env.sh]` Executes shell commands on the host environment

## Verification
- Run: `./tools/configure.sh maple:nsh && make`
