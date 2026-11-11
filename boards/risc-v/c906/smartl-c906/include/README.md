# `smartl-c906/include` Component (`boards/risc-v/c906/smartl-c906/include`)

## Overview
Board-level public headers (`include`) for `smartl-c906` (`risc-v/c906`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:c906_boardinitialize]` Public declaration `c906_boardinitialize()`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh smartl-c906:nsh && make`
