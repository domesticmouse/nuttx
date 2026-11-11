# `gd32vw553-hmq/include` Component (`boards/risc-v/gd32vw55x/gd32vw553-hmq/include`)

## Overview
Board-level public headers (`include`) for `gd32vw553-hmq` (`risc-v/gd32vw55x`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_HXTAL_FREQUENCY]` Hardware/board configuration macros (`BOARD_HXTAL_FREQUENCY`, `BOARD_IRC32K_FREQUENCY`, `BOARD_SYSCLK_FREQUENCY`, `BOARD_UART2_TX_GPIO`, `BOARD_UART2_TX_PIN`, `BOARD_UART2_TX_AF` (+37 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh gd32vw553-hmq:nsh && make`
