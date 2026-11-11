# `hpm6750evk2/include` Component (`boards/risc-v/hpm6750/hpm6750evk2/include`)

## Overview
Board-level public headers (`include`) for `hpm6750evk2` (`risc-v/hpm6750`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:hpm6750_boardinitialize]` Public declaration `hpm6750_boardinitialize()`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh hpm6750evk2:nsh && make`
