# `qemu-i486/include` Component (`boards/x86/qemu/qemu-i486/include`)

## Overview
Board-level public headers (`include`) for `qemu-i486` (`x86/qemu`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:PIT_CLOCK]` Hardware/board configuration macros (`PIT_CLOCK`)

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh qemu-i486:nsh && make`
