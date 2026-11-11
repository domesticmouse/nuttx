# `mcu123-lpc214x/scripts` Component (`boards/arm/lpc214x/mcu123-lpc214x/scripts`)

## Overview
Board support component `scripts` for `mcu123-lpc214x` (`arm/lpc214x`), containing 1 source/script file(s) (`lpc21isp.sh`).

## Interface
- `[lpc21isp.sh]` Shell script entry point `lpc21isp.sh`

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_WINDOWS_CYGWIN`

## Side Effects
- `[lpc21isp.sh]` Invokes host utilities (`lpc21isp`) to flash, debug, or test firmware

## Verification
- Run: `./tools/configure.sh mcu123-lpc214x:nsh && make`
