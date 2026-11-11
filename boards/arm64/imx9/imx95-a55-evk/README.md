# `imx95-a55-evk` Board Support Package (`boards/arm64/imx9/imx95-a55-evk`)

## Overview
Board Support Package (BSP) blueprint for `imx95-a55-evk` (`arm64` / `imx9`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `emmc`, `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `imx95-a55-evk` (`arm64/imx9`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 2 header file(s). Key symbols: `[board.h:IOMUX_LPI2C_DEFAULT]` Hardware/board configuration macros (`IOMUX_LPI2C_DEFAULT`, `IOMUX_LPSPI_DEFAULT`, `IOMUX_GPIO_DEFAULT`, `MUX_LPUART1_RX`, `MUX_LPUART1_TX`, `FLEXIO1_PWM0_MUX` (+69 more)), `[board_memorymap.h]` Board header declarations `board_memorymap.h`.
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `imx95-a55-evk` (`arm64/imx9`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 5 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
