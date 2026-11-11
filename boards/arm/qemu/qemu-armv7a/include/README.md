# `qemu-armv7a/include` Component (`boards/arm/qemu/qemu-armv7a/include`)

## Overview
Board-level public headers (`include`) for `qemu-armv7a` (`arm/qemu`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h]` Board header declarations `board.h`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh qemu-armv7a:nsh && make`
