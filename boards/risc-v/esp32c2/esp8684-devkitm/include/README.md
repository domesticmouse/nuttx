# `esp8684-devkitm/include` Component (`boards/risc-v/esp32c2/esp8684-devkitm/include`)

## Overview
Board-level public headers (`include`) for `esp8684-devkitm` (`risc-v/esp32c2`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_NGPIOOUT]` Hardware/board configuration macros (`BOARD_NGPIOOUT`, `BOARD_NGPIOINT`, `BUTTON_BOOT`, `LED_RED`, `LED_GREEN`, `LED_BLUE`)

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh esp8684-devkitm:nsh && make`
