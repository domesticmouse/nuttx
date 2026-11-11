# `qemu-intel64/include` Component (`boards/x86_64/qemu/qemu-intel64/include`)

## Overview
Board-level public headers (`include`) for `qemu-intel64` (`x86_64/qemu`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:PIT_CLOCK]` Hardware/board configuration macros (`PIT_CLOCK`)

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh qemu-intel64:nsh && make`
