# `open1788/tools` Component (`boards/arm/lpc17xx_40xx/open1788/tools`)

## Overview
Board support component `tools` for `open1788` (`arm/lpc17xx_40xx`), containing 1 source/script file(s) (`oocd.sh`).

## Interface
- `[oocd.sh]` Shell script entry point `oocd.sh`

## Invariants
- `[oocd.sh:exit]` Validates required environment variables, arguments, or files before execution

## Side Effects
- `[oocd.sh]` Invokes host utilities (`openocd`) to flash, debug, or test firmware

## Verification
- Run: `./tools/configure.sh open1788:nsh && make`
