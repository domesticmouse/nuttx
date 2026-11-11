# `freedom-kl25z` Board Support Package (`boards/arm/kl/freedom-kl25z`)

## Overview
Board Support Package (BSP) blueprint for `freedom-kl25z` (`arm` / `kl`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `freedom-kl25z` (`arm/kl`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:kl_tsi_initialize]` Public declaration `kl_tsi_initialize()`, `[board.h:BOARD_XTAL_FREQ]` Hardware/board configuration macros (`BOARD_XTAL_FREQ`, `BOARD_XTAL32_FREQ`, `BOARD_PRDIV0`, `BOARD_VDIV0`, `BOARD_PLLIN_FREQ`, `BOARD_PLLOUT_FREQ` (+40 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `freedom-kl25z` (`arm/kl`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 7 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
