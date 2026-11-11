# `dk-tm4c129x/tools` Component (`boards/arm/tiva/dk-tm4c129x/tools`)

## Overview
Board support component `tools` for `dk-tm4c129x` (`arm/tiva`), containing 1 source/script file(s) (`oocd.sh`).

## Interface
- `[oocd.sh]` Shell script entry point `oocd.sh`

## Invariants
- `[oocd.sh:exit]` Validates required environment variables, arguments, or files before execution

## Side Effects
- `[oocd.sh]` Invokes host utilities (`openocd`) to flash, debug, or test firmware

## Verification
- Run: `./tools/configure.sh dk-tm4c129x:nsh && make`
