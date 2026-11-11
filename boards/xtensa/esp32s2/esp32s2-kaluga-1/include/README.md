# `esp32s2-kaluga-1/include` Component (`boards/xtensa/esp32s2/esp32s2-kaluga-1/include`)

## Overview
Board-level public headers (`include`) for `esp32s2-kaluga-1` (`xtensa/esp32s2`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_XTAL_FREQUENCY]` Hardware/board configuration macros (`BOARD_XTAL_FREQUENCY`, `BOARD_CLOCK_FREQUENCY`, `BUTTON_BTN1`, `BUTTON_BTN1_BIT`, `BUTTON_BTN2`, `BUTTON_BTN2_BIT` (+29 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh esp32s2-kaluga-1:nsh && make`
