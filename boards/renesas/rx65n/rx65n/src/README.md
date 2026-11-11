# `rx65n/src` Component (`boards/renesas/rx65n/rx65n/src`)

## Overview
Board-level C implementation (`src`) for `rx65n` (`renesas/rx65n`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 1 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[rx65n_main.c:board_autoled1_on]` Public function `board_autoled1_on()`
- `[rx65n_main.c:board_autoled2_on]` Public function `board_autoled2_on()`
- `[rx65n_main.c:board_autoled_on]` Public function `board_autoled_on()`
- `[rx65n_main.c:board_autoled1_off]` Public function `board_autoled1_off()`
- `[rx65n_main.c:board_autoled2_off]` Public function `board_autoled2_off()`
- `[rx65n_main.c:board_autoled_off]` Public function `board_autoled_off()`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh rx65n:nsh && make`
