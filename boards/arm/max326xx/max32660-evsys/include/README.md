# `max32660-evsys/include` Component (`boards/arm/max326xx/max32660-evsys/include`)

## Overview
Board-level public headers (`include`) for `max32660-evsys` (`arm/max326xx`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_HAVE_X32K]` Hardware/board configuration macros (`BOARD_HAVE_X32K`, `BOARD_LED`, `BOARD_NLEDS`, `BOARD_LED_BIT`, `LED_STARTED`, `LED_HEAPALLOCATE` (+17 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh max32660-evsys:nsh && make`
