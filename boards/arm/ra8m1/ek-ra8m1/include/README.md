# `ek-ra8m1/include` Component (`boards/arm/ra8m1/ek-ra8m1/include`)

## Overview
Board-level public headers (`include`) for `ek-ra8m1` (`arm/ra8m1`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_HOCO_FREQUENCY]` Hardware/board configuration macros (`BOARD_HOCO_FREQUENCY`, `BOARD_MOSC_FREQUENCY`, `BOARD_MOSC_EXTERNAL_CLOCK`, `BOARD_MOSC_STABILIZATION_US`, `BOARD_SYSCLK_SOURCE`, `BOARD_PLL1_SOURCE` (+102 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh ek-ra8m1:nsh && make`
