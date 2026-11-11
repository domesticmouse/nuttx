# `csk6011a-nano/src` Component (`boards/arm/csk6/csk6011a-nano/src`)

## Overview
Board-level C implementation (`src`) for `csk6011a-nano` (`arm/csk6`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 1 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[csk6011a_nano_boardinit.c:board_late_initialize]` Public function `board_late_initialize()`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh csk6011a-nano:nsh && make`
