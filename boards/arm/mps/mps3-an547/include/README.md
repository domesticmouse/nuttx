# `mps3-an547/include` Component (`boards/arm/mps/mps3-an547/include`)

## Overview
Board-level public headers (`include`) for `mps3-an547` (`arm/mps`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:MPS_SYSTICK_CLOCK]` Hardware/board configuration macros (`MPS_SYSTICK_CLOCK`)

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh mps3-an547:nsh && make`
