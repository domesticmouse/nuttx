# `z80sim/include` Component (`boards/z80/z80/z80sim/include`)

## Overview
Board-level public headers (`include`) for `z80sim` (`z80/z80`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h]` Board header declarations `board.h`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh z80sim:nsh && make`
