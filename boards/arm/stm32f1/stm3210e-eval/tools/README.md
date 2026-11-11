# `stm3210e-eval/tools` Component (`boards/arm/stm32f1/stm3210e-eval/tools`)

## Overview
Board support component `tools` for `stm3210e-eval` (`arm/stm32f1`), containing 1 source/script file(s) (`oocd.sh`).

## Interface
- `[oocd.sh]` Shell script entry point `oocd.sh`

## Invariants
- `[oocd.sh:exit]` Validates required environment variables, arguments, or files before execution

## Side Effects
- `[oocd.sh]` Invokes host utilities (`openocd`) to flash, debug, or test firmware

## Verification
- Run: `./tools/configure.sh stm3210e-eval:nsh && make`
