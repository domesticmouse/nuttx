# `star64/src` Component (`boards/risc-v/jh7110/star64/src`)

## Overview
Board-level C implementation (`src`) for `star64` (`risc-v/jh7110`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 1 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[jh7110_boardinit.c:mount_ramdisk]` Public function `mount_ramdisk()`
- `[jh7110_boardinit.c:board_late_initialize]` Public function `board_late_initialize()`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh star64:nsh && make`
