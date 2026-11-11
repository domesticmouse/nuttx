# `fvp-armv8r-aarch32/include` Component (`boards/arm/fvp-v8r-aarch32/fvp-armv8r-aarch32/include`)

## Overview
Board-level public headers (`include`) for `fvp-armv8r-aarch32` (`arm/fvp-v8r-aarch32`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 2 header file(s).

## Interface
- `[board.h]` Board header declarations `board.h`
- `[board_memorymap.h]` Board header declarations `board_memorymap.h`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh fvp-armv8r-aarch32:nsh && make`
