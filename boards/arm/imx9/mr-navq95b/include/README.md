# `mr-navq95b/include` Component (`boards/arm/imx9/mr-navq95b/include`)

## Overview
Board-level public headers (`include`) for `mr-navq95b` (`arm/imx9`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:BOARD_XTAL_FREQUENCY]` Hardware/board configuration macros (`BOARD_XTAL_FREQUENCY`, `BOARD_CPU_FREQUENCY`, `LPUART2_CLK`, `LPUART5_CLK`, `LPI2C1_CLK`, `LPI2C4_CLK` (+53 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh mr-navq95b:nsh && make`
