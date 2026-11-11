# `lichee-rv-86-panel/src` Component (`boards/risc-v/allwinner-d1/lichee-rv-86-panel/src`)

## Overview
Board-level C implementation (`src`) for `lichee-rv-86-panel` (`risc-v/allwinner-d1`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 1 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[allwinner_d1_boardinit.c:board_late_initialize]` Public function `board_late_initialize()`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh lichee-rv-86-panel:nsh && make`
