# `samd21-xplained` Board Support Package (`boards/arm/samd2l2/samd21-xplained`)

## Overview
Board Support Package (BSP) blueprint for `samd21-xplained` (`arm` / `samd2l2`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `samd21-xplained` (`arm/samd2l2`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:BOARD_XOSC_FREQUENCY]` Hardware/board configuration macros (`BOARD_XOSC_FREQUENCY`, `BOARD_XOSC_STARTUPTIME`, `BOARD_XOSC_ISCRYSTAL`, `BOARD_XOSC_AMPGC`, `BOARD_XOSC_ONDEMAND`, `BOARD_XOSC32K_FREQUENCY` (+124 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `samd21-xplained` (`arm/samd2l2`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 8 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
