# `n32h762iil7` Board Support Package (`boards/arm/n32h7/n32h762iil7`)

## Overview
Board Support Package (BSP) blueprint for `n32h762iil7` (`arm` / `n32h7`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `n32h762iil7` (`arm/n32h7`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:N32_BOARD_XTAL]` Hardware/board configuration macros (`N32_BOARD_XTAL`, `N32_HSI_FREQUENCY`, `N32_MSI_FREQUENCY`, `N32_LSI_FREQUENCY`, `N32_HSE_FREQUENCY`, `N32_LSE_FREQUENCY` (+85 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `n32h762iil7` (`arm/n32h7`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 15 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
