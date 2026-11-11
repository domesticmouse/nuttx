# `xiao-nrf52840` Board Support Package (`boards/arm/nrf52/xiao-nrf52840`)

## Overview
Board Support Package (BSP) blueprint for `xiao-nrf52840` (`arm` / `nrf52`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `jumbo`, `nsh`, `usbnsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `xiao-nrf52840` (`arm/nrf52`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:BOARD_SYSTICK_CLOCK]` Hardware/board configuration macros (`BOARD_SYSTICK_CLOCK`, `BOARD_LED1`, `BOARD_LED2`, `BOARD_LED3`, `BOARD_NLEDS`, `BOARD_LED1_BIT` (+12 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `xiao-nrf52840` (`arm/nrf52`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 8 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
