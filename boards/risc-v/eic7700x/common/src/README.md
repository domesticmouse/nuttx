# `common/src` Component (`boards/risc-v/eic7700x/common/src`)

## Overview
Board-level C implementation (`src`) for `common` (`risc-v/eic7700x`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 1 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[eic7700x_boot.c:board_late_initialize]` Public function `board_late_initialize()`

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_BOARD_COMMON`

## Side Effects
- `[eic7700x_boot.c:board_late_initialize]` Initializes/registers kernel devices or filesystems (`eic7700x_cpuclk_initialize()`)

## Verification
- Run: `./tools/configure.sh sim:nsh && make`
