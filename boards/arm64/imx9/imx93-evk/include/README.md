# `imx93-evk/include` Component (`boards/arm64/imx9/imx93-evk/include`)

## Overview
Board-level public headers (`include`) for `imx93-evk` (`arm64/imx9`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 5 header file(s).

## Interface
- `[bin_romfsimg.h]` Board header declarations `bin_romfsimg.h`
- `[board.h:IOMUX_LPI2C_DEFAULT]` Hardware/board configuration macros (`IOMUX_LPI2C_DEFAULT`, `IOMUX_LPSPI_DEFAULT`, `IOMUX_GPIO_DEFAULT`, `MUX_LPUART1_RX`, `MUX_LPUART1_TX`, `FLEXIO1_PWM0_MUX` (+56 more))
- `[board_memorymap.h]` Board header declarations `board_memorymap.h`
- `[imx9_ddr_training.h:FILE_DMEM_1D]` Hardware/board configuration macros (`FILE_DMEM_1D`, `FILE_DMEM_2D`, `FILE_IMEM_1D`, `FILE_IMEM_2D`)
- `[imx9_trdc_config.h:RWX]` Hardware/board configuration macros (`RWX`, `TEE_SHM_SIZE`)

## Invariants
- `[board.h:#error]` Compile-time guard: `ENET1 supports only RMII and RGMII`

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh imx93-evk:nsh && make`
