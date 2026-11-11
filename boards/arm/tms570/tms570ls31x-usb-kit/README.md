# `tms570ls31x-usb-kit` Board Support Package (`boards/arm/tms570/tms570ls31x-usb-kit`)

## Overview
Board Support Package (BSP) blueprint for `tms570ls31x-usb-kit` (`arm` / `tms570`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `tms570ls31x-usb-kit` (`arm/tms570`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:BOARD_FCLKIN_FREQUENCY]` Hardware/board configuration macros (`BOARD_FCLKIN_FREQUENCY`, `BOARD_PLL_NR`, `BOARD_PLL_NF`, `BOARD_PLL_OD`, `BOARD_PLL_R`, `BOARD_PLL_FREQUENCY` (+34 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `tms570ls31x-usb-kit` (`arm/tms570`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 8 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
