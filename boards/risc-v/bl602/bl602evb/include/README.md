# `bl602evb/include` Component (`boards/risc-v/bl602/bl602evb/include`)

## Overview
Board-level public headers (`include`) for `bl602evb` (`risc-v/bl602`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:bl602_boardinitialize]` Public declaration `bl602_boardinitialize()`
- `[board.h:BOARD_NGPIOIN]` Hardware/board configuration macros (`BOARD_NGPIOIN`, `BOARD_NGPIOOUT`, `BOARD_NGPIOINT`, `BOARD_GPIO_IN1`, `BOARD_GPIO_OUT1`, `BOARD_GPIO_INT1` (+15 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh bl602evb:nsh && make`
