# `esp32s2-saola-1/include` Component (`boards/xtensa/esp32s2/esp32s2-saola-1/include`)

## Overview
Board-level public headers (`include`) for `esp32s2-saola-1` (`xtensa/esp32s2`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_XTAL_FREQUENCY]` Hardware/board configuration macros (`BOARD_XTAL_FREQUENCY`, `BOARD_CLOCK_FREQUENCY`, `BUTTON_BTN1`, `BUTTON_BTN1_BIT`, `NUM_BUTTONS`, `BOARD_NLEDS` (+3 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh esp32s2-saola-1:nsh && make`
