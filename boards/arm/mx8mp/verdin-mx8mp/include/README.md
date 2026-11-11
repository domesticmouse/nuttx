# `verdin-mx8mp/include` Component (`boards/arm/mx8mp/verdin-mx8mp/include`)

## Overview
Board-level public headers (`include`) for `verdin-mx8mp` (`arm/mx8mp`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:IOMUX_CONSOLE_UART_RX]` Hardware/board configuration macros (`IOMUX_CONSOLE_UART_RX`, `IOMUX_CONSOLE_UART_TX`, `BOARD_LED_1`, `BOARD_LED_2`, `BOARD_LED_3`, `BOARD_LED_4` (+17 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh verdin-mx8mp:nsh && make`
