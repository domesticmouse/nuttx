# `imx95-evk/include` Component (`boards/arm/imx9/imx95-evk/include`)

## Overview
Board-level public headers (`include`) for `imx95-evk` (`arm/imx9`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_XTAL_FREQUENCY]` Hardware/board configuration macros (`BOARD_XTAL_FREQUENCY`, `BOARD_CPU_FREQUENCY`, `LPUART3_CLK`, `LPI2C6_CLK`, `LPSPI1_CLK`, `FLEXCAN1_CLK` (+35 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh imx95-evk:nsh && make`
