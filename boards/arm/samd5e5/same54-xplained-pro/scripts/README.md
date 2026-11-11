# `same54-xplained-pro/scripts` Component (`boards/arm/samd5e5/same54-xplained-pro/scripts`)

## Overview
Board support component `scripts` for `same54-xplained-pro` (`arm/samd5e5`), containing 1 source/script file(s) (`nvm.c`).

## Interface
- `[nvm.c:main]` Public function `main()`

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_SAME54_XPLAINED_PRO_RUNFROMFLASH`, `CONFIG_SAME54_XPLAINED_PRO_RUNFROMSRAM`

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh same54-xplained-pro:nsh && make`
