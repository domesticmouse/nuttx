# `xiao-seeeduino/include` Component (`boards/arm/samd2l2/xiao-seeeduino/include`)

## Overview
Board-level public headers (`include`) for `xiao-seeeduino` (`arm/samd2l2`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_XOSC_FREQUENCY]` Hardware/board configuration macros (`BOARD_XOSC_FREQUENCY`, `BOARD_XOSC_STARTUPTIME`, `BOARD_XOSC_ISCRYSTAL`, `BOARD_XOSC_AMPGC`, `BOARD_XOSC_ONDEMAND`, `BOARD_XOSC32K_FREQUENCY` (+89 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh xiao-seeeduino:nsh && make`
