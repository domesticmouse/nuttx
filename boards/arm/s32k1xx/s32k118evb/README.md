# `s32k118evb` Board Support Package (`boards/arm/s32k1xx/s32k118evb`)

## Overview
Board Support Package (BSP) blueprint for `s32k118evb` (`arm` / `s32k1xx`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `s32k118evb` (`arm/s32k1xx`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:BOARD_XTAL_FREQUENCY]` Hardware/board configuration macros (`BOARD_XTAL_FREQUENCY`, `BOARD_LED_R`, `BOARD_LED_G`, `BOARD_LED_B`, `BOARD_NLEDS`, `BOARD_LED_R_BIT` (+23 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `s32k118evb` (`arm/s32k1xx`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 10 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
