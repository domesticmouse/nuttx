# `nrf52-feather` Board Support Package (`boards/arm/nrf52/nrf52-feather`)

## Overview
Board Support Package (BSP) blueprint for `nrf52-feather` (`arm` / `nrf52`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `i2c`, `nsh`, `userleds`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `nrf52-feather` (`arm/nrf52`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:BOARD_SYSTICK_CLOCK]` Hardware/board configuration macros (`BOARD_SYSTICK_CLOCK`, `BOARD_LED1`, `BOARD_LED2`, `BOARD_NLEDS`, `BOARD_LED1_BIT`, `BOARD_LED2_BIT` (+12 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `nrf52-feather` (`arm/nrf52`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 6 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
