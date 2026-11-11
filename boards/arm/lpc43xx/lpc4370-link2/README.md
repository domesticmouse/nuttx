# `lpc4370-link2` Board Support Package (`boards/arm/lpc43xx/lpc4370-link2`)

## Overview
Board Support Package (BSP) blueprint for `lpc4370-link2` (`arm` / `lpc43xx`). Coordinates board initialization, headers, and tooling across `include, scripts, src`. Includes build configurations: `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `lpc4370-link2` (`arm/lpc43xx`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:BOARD_XTAL_FREQUENCY]` Hardware/board configuration macros (`BOARD_XTAL_FREQUENCY`, `BOARD_RTCCLK_FREQUENCY`, `BOARD_INTRCOSC_FREQUENCY`, `BOARD_PLL_MSEL`, `BOARD_PLL_NSEL`, `BOARD_PLL_PSEL` (+80 more)).
- [`scripts`](./scripts/README.md) - Board support component `scripts` for `lpc4370-link2` (`arm/lpc43xx`), containing 1 source/script file(s) (`flash.sh`). Key symbols: `[flash.sh]` Shell script entry point `flash.sh`.
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `lpc4370-link2` (`arm/lpc43xx`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 6 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
