# `nrf54l15-tag` Board Support Package (`boards/arm/nrf54l/nrf54l15-tag`)

## Overview
Board Support Package (BSP) blueprint for `nrf54l15-tag` (`arm` / `nrf54l`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`, `sdc`, `sensors`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `nrf54l15-tag` (`arm/nrf54l`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:BOARD_SYSTICK_CLOCK]` Hardware/board configuration macros (`BOARD_SYSTICK_CLOCK`, `BOARD_HFXO_CAPACITANCE`, `BOARD_LED1`, `BOARD_LED2`, `BOARD_LED3`, `BOARD_NLEDS` (+19 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `nrf54l15-tag` (`arm/nrf54l`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 10 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
