# `sim/include` Component (`boards/sim/sim/sim/include`)

## Overview
Board-level public headers (`include`) for `sim` (`sim/sim`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h]` Board header declarations `board.h`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh sim:nsh && make`
