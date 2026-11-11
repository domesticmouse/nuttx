# `z16f2800100zcog/src` Component (`boards/z16/z16f/z16f2800100zcog/src`)

## Overview
Board-level C implementation (`src`) for `z16f2800100zcog` (`z16/z16f`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 2 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[z16f_boot.c:z16f_board_initialize]` Public function `z16f_board_initialize()`
- `[z16f_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[z16f_leds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[z16f_leds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[z16f_leds.c:board_autoled_off]` Public function `board_autoled_off()`

## Invariants
- None

## Side Effects
- `[z16f_boot.c:z16f_board_initialize]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[z16f_leds.c:board_autoled_initialize]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)

## Verification
- Run: `./tools/configure.sh z16f2800100zcog:nsh && make`
