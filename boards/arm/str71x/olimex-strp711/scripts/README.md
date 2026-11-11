# `olimex-strp711/scripts` Component (`boards/arm/str71x/olimex-strp711/scripts`)

## Overview
Board support component `scripts` for `olimex-strp711` (`arm/str71x`), containing 1 source/script file(s) (`oocd.sh`).

## Interface
- `[oocd.sh]` Shell script entry point `oocd.sh`

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_WINDOWS_CYGWIN`
- `[oocd.sh:exit]` Validates required environment variables, arguments, or files before execution

## Side Effects
- `[oocd.sh]` Invokes host utilities (`openocd`) to flash, debug, or test firmware

## Verification
- Run: `./tools/configure.sh olimex-strp711:nsh && make`
