# `ek-ra8m1` Board Support Package (`boards/arm/ra8m1/ek-ra8m1`)

## Overview
Board Support Package (BSP) blueprint for `ek-ra8m1` (`arm` / `ra8m1`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`, `nsh-leds`, `serial-test`, `timer-gpio`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `ek-ra8m1` (`arm/ra8m1`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:BOARD_HOCO_FREQUENCY]` Hardware/board configuration macros (`BOARD_HOCO_FREQUENCY`, `BOARD_MOSC_FREQUENCY`, `BOARD_MOSC_EXTERNAL_CLOCK`, `BOARD_MOSC_STABILIZATION_US`, `BOARD_SYSCLK_SOURCE`, `BOARD_PLL1_SOURCE` (+102 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `ek-ra8m1` (`arm/ra8m1`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 6 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
