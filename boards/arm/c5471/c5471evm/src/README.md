# `c5471evm/src` Component (`boards/arm/c5471/c5471evm/src`)

## Overview
Board-level C implementation (`src`) for `c5471evm` (`arm/c5471`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 1 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[c5471_leds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[c5471_leds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[c5471_leds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[c5471_leds.c:board_late_initialize]` Public function `board_late_initialize()`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh c5471evm:nsh && make`
