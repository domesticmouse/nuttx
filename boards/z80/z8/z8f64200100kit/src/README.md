# `z8f64200100kit/src` Component (`boards/z80/z8/z8f64200100kit/src`)

## Overview
Board-level C implementation (`src`) for `z8f64200100kit` (`z80/z8`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 2 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[z8_boot.c:z8_board_initialize]` Public function `z8_board_initialize()`
- `[z8_leds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[z8_leds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[z8_leds.c:board_autoled_off]` Public function `board_autoled_off()`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh z8f64200100kit:ostest && make`
