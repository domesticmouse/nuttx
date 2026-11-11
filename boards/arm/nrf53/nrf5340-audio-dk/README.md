# `nrf5340-audio-dk` Board Support Package (`boards/arm/nrf53/nrf5340-audio-dk`)

## Overview
Board Support Package (BSP) blueprint for `nrf5340-audio-dk` (`arm` / `nrf53`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh_cpuapp`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `nrf5340-audio-dk` (`arm/nrf53`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:BOARD_SYSTICK_CLOCK]` Hardware/board configuration macros (`BOARD_SYSTICK_CLOCK`, `BOARD_LED1`, `BOARD_LED2`, `BOARD_LED3`, `BOARD_NLEDS`, `BOARD_LED1_BIT` (+25 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `nrf5340-audio-dk` (`arm/nrf53`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 5 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
