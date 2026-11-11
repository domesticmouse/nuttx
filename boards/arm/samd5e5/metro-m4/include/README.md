# `metro-m4/include` Component (`boards/arm/samd5e5/metro-m4/include`)

## Overview
Board-level public headers (`include`) for `metro-m4` (`arm/samd5e5`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_OSC32K_FREQUENCY]` Hardware/board configuration macros (`BOARD_OSC32K_FREQUENCY`, `BOARD_XOSC32K_FREQUENCY`, `BOARD_DFLL_FREQUENCY`, `BOARD_XOSC0_FREQUENCY`, `BOARD_XOSC1_FREQUENCY`, `BOARD_DPLL0_FREQUENCY` (+222 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh metro-m4:nsh && make`
