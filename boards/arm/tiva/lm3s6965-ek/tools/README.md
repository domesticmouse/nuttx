# `lm3s6965-ek/tools` Component (`boards/arm/tiva/lm3s6965-ek/tools`)

## Overview
Board support component `tools` for `lm3s6965-ek` (`arm/tiva`), containing 1 source/script file(s) (`oocd.sh`).

## Interface
- `[oocd.sh]` Shell script entry point `oocd.sh`

## Invariants
- `[oocd.sh:exit]` Validates required environment variables, arguments, or files before execution

## Side Effects
- `[oocd.sh]` Invokes host utilities (`openocd`) to flash, debug, or test firmware

## Verification
- Run: `./tools/configure.sh lm3s6965-ek:nsh && make`
