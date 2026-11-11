# `imx93-qsb/include` Component (`boards/arm/imx9/imx93-qsb/include`)

## Overview
Board-level public headers (`include`) for `imx93-qsb` (`arm/imx9`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_XTAL_FREQUENCY]` Hardware/board configuration macros (`BOARD_XTAL_FREQUENCY`, `BOARD_CPU_FREQUENCY`, `LPUART2_CLK`, `IOMUX_LPI2C_DEFAULT`, `IOMUX_LPSPI_DEFAULT`, `IOMUX_GPIO_DEFAULT` (+2 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh imx93-qsb:nsh && make`
