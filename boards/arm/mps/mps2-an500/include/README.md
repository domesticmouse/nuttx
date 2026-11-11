# `mps2-an500/include` Component (`boards/arm/mps/mps2-an500/include`)

## Overview
Board-level public headers (`include`) for `mps2-an500` (`arm/mps`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:MPS_SYSTICK_CLOCK]` Hardware/board configuration macros (`MPS_SYSTICK_CLOCK`)

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh mps2-an500:nsh && make`
