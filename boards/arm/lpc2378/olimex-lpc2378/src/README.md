# `olimex-lpc2378/src` Component (`boards/arm/lpc2378/olimex-lpc2378/src`)

## Overview
Board-level C implementation (`src`) for `olimex-lpc2378` (`arm/lpc2378`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 1 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[lpc2378_leds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[lpc2378_leds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[lpc2378_leds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[lpc2378_leds.c:lpc2378_statledoff]` Public function `lpc2378_statledoff()`
- `[lpc2378_leds.c:lpc2378_statledon]` Public function `lpc2378_statledon()`
- `[lpc2378_leds.c:board_late_initialize]` Public function `board_late_initialize()`

## Invariants
- None

## Side Effects
- `[lpc2378_leds.c:board_autoled_initialize]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)

## Verification
- Run: `./tools/configure.sh olimex-lpc2378:nsh && make`
