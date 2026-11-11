# `qemu-armv8a/include` Component (`boards/arm64/qemu/qemu-armv8a/include`)

## Overview
Board-level public headers (`include`) for `qemu-armv8a` (`arm64/qemu`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 2 header file(s).

## Interface
- `[board.h]` Board header declarations `board.h`
- `[board_memorymap.h]` Board header declarations `board_memorymap.h`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh qemu-armv8a:nsh && make`
