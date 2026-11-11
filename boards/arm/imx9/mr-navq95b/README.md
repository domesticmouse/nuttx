# `mr-navq95b` Board Support Package (`boards/arm/imx9/mr-navq95b`)

## Overview
Board Support Package (BSP) blueprint for `mr-navq95b` (`arm` / `imx9`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`, `rpmsg`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `mr-navq95b` (`arm/imx9`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:BOARD_XTAL_FREQUENCY]` Hardware/board configuration macros (`BOARD_XTAL_FREQUENCY`, `BOARD_CPU_FREQUENCY`, `LPUART2_CLK`, `LPUART5_CLK`, `LPI2C1_CLK`, `LPI2C4_CLK` (+53 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `mr-navq95b` (`arm/imx9`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 5 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
