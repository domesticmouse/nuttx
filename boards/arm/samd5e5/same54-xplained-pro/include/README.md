# `same54-xplained-pro/include` Component (`boards/arm/samd5e5/same54-xplained-pro/include`)

## Overview
Board-level public headers (`include`) for `same54-xplained-pro` (`arm/samd5e5`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_OSC32K_FREQUENCY]` Hardware/board configuration macros (`BOARD_OSC32K_FREQUENCY`, `BOARD_XOSC32K_FREQUENCY`, `BOARD_DFLL_FREQUENCY`, `BOARD_XOSC0_FREQUENCY`, `BOARD_XOSC1_FREQUENCY`, `BOARD_DPLL0_FREQUENCY` (+215 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh same54-xplained-pro:nsh && make`
