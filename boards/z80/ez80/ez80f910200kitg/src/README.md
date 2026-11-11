# `ez80f910200kitg/src` Component (`boards/z80/ez80/ez80f910200kitg/src`)

## Overview
Board-level C implementation (`src`) for `ez80f910200kitg` (`z80/ez80`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 2 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[ez80_boot.c:ez80_board_initialize]` Public function `ez80_board_initialize()`
- `[ez80_leds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[ez80_leds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[ez80_leds.c:board_autoled_off]` Public function `board_autoled_off()`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh ez80f910200kitg:ostest && make`
