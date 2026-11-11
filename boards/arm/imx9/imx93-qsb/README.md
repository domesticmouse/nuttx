# `imx93-qsb` Board Support Package (`boards/arm/imx9/imx93-qsb`)

## Overview
Board Support Package (BSP) blueprint for `imx93-qsb` (`arm` / `imx9`). Coordinates board initialization, headers, and tooling across `include, src, tools`. Includes build configurations: `nsh`, `nsh-ddr`, `rpmsg`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `imx93-qsb` (`arm/imx9`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:BOARD_XTAL_FREQUENCY]` Hardware/board configuration macros (`BOARD_XTAL_FREQUENCY`, `BOARD_CPU_FREQUENCY`, `LPUART2_CLK`, `IOMUX_LPI2C_DEFAULT`, `IOMUX_LPSPI_DEFAULT`, `IOMUX_GPIO_DEFAULT` (+2 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `imx93-qsb` (`arm/imx9`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 3 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
- [`tools`](./tools/README.md) - Board support component `tools` for `imx93-qsb` (`arm/imx9`), containing 1 source/script file(s) (`enable_onboard_debug.py`). Key symbols: `[enable_onboard_debug.py:set_bit]` Python function `set_bit(value, bit)`, `[enable_onboard_debug.py:clear_bit]` Python function `clear_bit(value, bit)`.
