# `metro-m4` Board Support Package (`boards/arm/samd5e5/metro-m4`)

## Overview
Board Support Package (BSP) blueprint for `metro-m4` (`arm` / `samd5e5`). Coordinates board initialization, headers, and tooling across `include, scripts, src`. Includes build configurations: `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `metro-m4` (`arm/samd5e5`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:BOARD_OSC32K_FREQUENCY]` Hardware/board configuration macros (`BOARD_OSC32K_FREQUENCY`, `BOARD_XOSC32K_FREQUENCY`, `BOARD_DFLL_FREQUENCY`, `BOARD_XOSC0_FREQUENCY`, `BOARD_XOSC1_FREQUENCY`, `BOARD_DPLL0_FREQUENCY` (+222 more)).
- [`scripts`](./scripts/README.md) - Board support component `scripts` for `metro-m4` (`arm/samd5e5`), containing 1 source/script file(s) (`nvm.c`). Key symbols: `[nvm.c:main]` Public function `main()`.
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `metro-m4` (`arm/samd5e5`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 15 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
