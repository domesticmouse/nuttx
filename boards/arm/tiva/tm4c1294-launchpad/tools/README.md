# `tm4c1294-launchpad/tools` Component (`boards/arm/tiva/tm4c1294-launchpad/tools`)

## Overview
Board support component `tools` for `tm4c1294-launchpad` (`arm/tiva`), containing 1 source/script file(s) (`oocd.sh`).

## Interface
- `[oocd.sh]` Shell script entry point `oocd.sh`

## Invariants
- `[oocd.sh:exit]` Validates required environment variables, arguments, or files before execution

## Side Effects
- `[oocd.sh]` Invokes host utilities (`openocd`) to flash, debug, or test firmware

## Verification
- Run: `./tools/configure.sh tm4c1294-launchpad:nsh && make`
