# `flipnclick-sam3x` Board Support Package (`boards/arm/sam34/flipnclick-sam3x`)

## Overview
Board Support Package (BSP) blueprint for `flipnclick-sam3x` (`arm` / `sam34`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`, `nxlines`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `flipnclick-sam3x` (`arm/sam34`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:BOARD_32KOSC_FREQUENCY]` Hardware/board configuration macros (`BOARD_32KOSC_FREQUENCY`, `BOARD_SCLK_FREQUENCY`, `BOARD_MAINOSC_FREQUENCY`, `BOARD_CKGR_MOR_MOSCXTST`, `BOARD_CKGR_PLLAR_MUL`, `BOARD_CKGR_PLLAR_COUNT` (+32 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `flipnclick-sam3x` (`arm/sam34`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 7 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
