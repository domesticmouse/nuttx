# `metro-m4/scripts` Component (`boards/arm/samd5e5/metro-m4/scripts`)

## Overview
Board support component `scripts` for `metro-m4` (`arm/samd5e5`), containing 1 source/script file(s) (`nvm.c`).

## Interface
- `[nvm.c:main]` Public function `main()`

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_METRO_M4_RUNFROMFLASH`, `CONFIG_METRO_M4_RUNFROMSRAM`

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh metro-m4:nsh && make`
