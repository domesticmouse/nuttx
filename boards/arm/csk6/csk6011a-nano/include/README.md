# `csk6011a-nano/include` Component (`boards/arm/csk6/csk6011a-nano/include`)

## Overview
Board-level public headers (`include`) for `csk6011a-nano` (`arm/csk6`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:CSK6_SYSTICK_CLOCK]` Hardware/board configuration macros (`CSK6_SYSTICK_CLOCK`)

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh csk6011a-nano:nsh && make`
