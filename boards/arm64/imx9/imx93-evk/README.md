# `imx93-evk` Board Support Package (`boards/arm64/imx9/imx93-evk`)

## Overview
Board Support Package (BSP) blueprint for `imx93-evk` (`arm64` / `imx9`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `bootloader`, `knsh`, `koptee`, `nsh`, `optee`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `imx93-evk` (`arm64/imx9`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 5 header file(s). Key symbols: `[bin_romfsimg.h]` Board header declarations `bin_romfsimg.h`, `[board.h:IOMUX_LPI2C_DEFAULT]` Hardware/board configuration macros (`IOMUX_LPI2C_DEFAULT`, `IOMUX_LPSPI_DEFAULT`, `IOMUX_GPIO_DEFAULT`, `MUX_LPUART1_RX`, `MUX_LPUART1_TX`, `FLEXIO1_PWM0_MUX` (+56 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `imx93-evk` (`arm64/imx9`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 9 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[imx93-evk.h:imx9_bringup]` Public declaration `imx9_bringup()`.
