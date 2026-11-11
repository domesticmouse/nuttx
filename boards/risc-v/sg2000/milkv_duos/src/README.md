# `milkv_duos/src` Component (`boards/risc-v/sg2000/milkv_duos/src`)

## Overview
Board-level C implementation (`src`) for `milkv_duos` (`risc-v/sg2000`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 1 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[sg2000_boardinit.c:board_late_initialize]` Public function `board_late_initialize()`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh milkv_duos:nsh && make`
