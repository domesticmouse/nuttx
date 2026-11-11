# `franzininho-wifi/include` Component (`boards/xtensa/esp32s2/franzininho-wifi/include`)

## Overview
Board-level public headers (`include`) for `franzininho-wifi` (`xtensa/esp32s2`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_XTAL_FREQUENCY]` Hardware/board configuration macros (`BOARD_XTAL_FREQUENCY`, `BOARD_CLOCK_FREQUENCY`, `BOARD_NLEDS`, `BOARD_NGPIOOUT`, `BOARD_NGPIOIN`, `BOARD_NGPIOINT`)

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh franzininho-wifi:nsh && make`
