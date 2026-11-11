# `gd32vw553k-start/include` Component (`boards/risc-v/gd32vw55x/gd32vw553k-start/include`)

## Overview
Board-level public headers (`include`) for `gd32vw553k-start` (`risc-v/gd32vw55x`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_HXTAL_FREQUENCY]` Hardware/board configuration macros (`BOARD_HXTAL_FREQUENCY`, `BOARD_IRC32K_FREQUENCY`, `BOARD_SYSCLK_FREQUENCY`, `BOARD_UART2_TX_GPIO`, `BOARD_UART2_TX_PIN`, `BOARD_UART2_TX_AF` (+43 more))

## Invariants
- `[board.h:#error]` Compile-time guard: `I2C1 and the I2C0 fallback (SPI on) both need PB15/PA8`

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh gd32vw553k-start:nsh && make`
