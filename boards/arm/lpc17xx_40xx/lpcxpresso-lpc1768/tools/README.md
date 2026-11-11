# `lpcxpresso-lpc1768/tools` Component (`boards/arm/lpc17xx_40xx/lpcxpresso-lpc1768/tools`)

## Overview
Board support component `tools` for `lpcxpresso-lpc1768` (`arm/lpc17xx_40xx`), containing 1 source/script file(s) (`flash.sh`).

## Interface
- `[flash.sh]` Shell script entry point `flash.sh`

## Invariants
- `[flash.sh:exit]` Validates required environment variables, arguments, or files before execution

## Side Effects
- `[flash.sh]` Invokes host utilities (`mv`, `rm`) to flash, debug, or test firmware

## Verification
- Run: `./tools/configure.sh lpcxpresso-lpc1768:nsh && make`
