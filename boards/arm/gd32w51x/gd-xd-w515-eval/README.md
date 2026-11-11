# `gd-xd-w515-eval` Board Support Package (`boards/arm/gd32w51x/gd-xd-w515-eval`)

## Overview
Board Support Package (BSP) blueprint for `gd-xd-w515-eval` (`arm` / `gd32w51x`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `littlefs`, `nsh`, `ostest`, `periph`, `pm`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `gd-xd-w515-eval` (`arm/gd32w51x`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:BOARD_HXTAL_FREQUENCY]` Hardware/board configuration macros (`BOARD_HXTAL_FREQUENCY`, `BOARD_IRC32K_FREQUENCY`, `BOARD_SYSCLK_FREQUENCY`, `BOARD_NLEDS`, `BOARD_LED1`, `BOARD_LED2` (+50 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `gd-xd-w515-eval` (`arm/gd32w51x`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 11 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
