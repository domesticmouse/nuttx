# `arduino-r4-minima/include` Component (`boards/arm/ra4/arduino-r4-minima/include`)

## Overview
Board-level public headers (`include`) for `arduino-r4-minima` (`arm/ra4`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:RA_CKSEL]` Hardware/board configuration macros (`RA_CKSEL`, `RA_HOCOEN`, `RA_HOCO_FREQUENCY`, `RA_ICK_DIV`, `RA_ICLK_FREQUENCY`, `RA_FCK_DIV` (+44 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh arduino-r4-minima:nsh && make`
