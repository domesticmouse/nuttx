# `ucans32k146` Board Support Package (`boards/arm/s32k1xx/ucans32k146`)

## Overview
Board Support Package (BSP) blueprint for `ucans32k146` (`arm` / `s32k1xx`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `can`, `nsh`, `se05x`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `ucans32k146` (`arm/s32k1xx`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:BOARD_XTAL_FREQUENCY]` Hardware/board configuration macros (`BOARD_XTAL_FREQUENCY`, `UCANS32K146_RUN_SYSCLK_FREQUENCY`, `BOARD_LED_R`, `BOARD_LED_G`, `BOARD_LED_B`, `BOARD_NLEDS` (+37 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `ucans32k146` (`arm/s32k1xx`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 11 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
