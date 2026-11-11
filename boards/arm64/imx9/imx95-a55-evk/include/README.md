# `imx95-a55-evk/include` Component (`boards/arm64/imx9/imx95-a55-evk/include`)

## Overview
Board-level public headers (`include`) for `imx95-a55-evk` (`arm64/imx9`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 2 header file(s).

## Interface
- `[board.h:IOMUX_LPI2C_DEFAULT]` Hardware/board configuration macros (`IOMUX_LPI2C_DEFAULT`, `IOMUX_LPSPI_DEFAULT`, `IOMUX_GPIO_DEFAULT`, `MUX_LPUART1_RX`, `MUX_LPUART1_TX`, `FLEXIO1_PWM0_MUX` (+69 more))
- `[board_memorymap.h]` Board header declarations `board_memorymap.h`

## Invariants
- `[board.h:#error]` Compile-time guard: `ENET1 supports only RMII and RGMII`

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh imx95-a55-evk:nsh && make`
