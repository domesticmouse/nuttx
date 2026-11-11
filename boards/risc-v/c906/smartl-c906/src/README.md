# `smartl-c906/src` Component (`boards/risc-v/c906/smartl-c906/src`)

## Overview
Board-level C implementation (`src`) for `smartl-c906` (`risc-v/c906`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 4 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[smartl-c906.h:c906_bringup]` Public declaration `c906_bringup()`
- `[c906_boot.c:c906_boardinitialize]` Public function `c906_boardinitialize()`
- `[c906_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[c906_bringup.c:c906_bringup]` Public function `c906_bringup()`
- `[c906_leds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[c906_leds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[c906_leds.c:board_autoled_off]` Public function `board_autoled_off()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_LEDS`

## Side Effects
- `[c906_boot.c:c906_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`)

## Verification
- Run: `./tools/configure.sh smartl-c906:nsh && make`
