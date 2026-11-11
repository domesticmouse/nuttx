# `rm57l843-launchxl2` Board Support Package (`boards/arm/rm57/rm57l843-launchxl2`)

## Overview
Board Support Package (BSP) blueprint for `rm57l843-launchxl2` (`arm` / `rm57`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `adc`, `buttons`, `can`, `candma`, `cansock`, `eth` (+9 more).

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `rm57l843-launchxl2` (`arm/rm57`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:BOARD_FCLKIN_FREQUENCY]` Hardware/board configuration macros (`BOARD_FCLKIN_FREQUENCY`, `BOARD_PLL_NR`, `BOARD_PLL_PLLMUL`, `BOARD_PLL_OD`, `BOARD_PLL_R`, `BOARD_PLL_FREQUENCY` (+37 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `rm57l843-launchxl2` (`arm/rm57`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 11 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
