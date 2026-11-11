# `avaota-a1/include` Component (`boards/arm64/a527/avaota-a1/include`)

## Overview
Board-level public headers (`include`) for `avaota-a1` (`arm64/a527`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 2 header file(s).

## Interface
- `[board.h]` Board header declarations `board.h`
- `[board_memorymap.h]` Board header declarations `board_memorymap.h`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh avaota-a1:nsh && make`
