# `pimoroni-pico-plus-2-w` Board Support Package (`boards/arm/rp23xx/pimoroni-pico-plus-2-w`)

## Overview
Board Support Package (BSP) blueprint for `pimoroni-pico-plus-2-w` (`arm` / `rp23xx`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`, `usbnsh`, `wifi`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `pimoroni-pico-plus-2-w` (`arm/rp23xx`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 5 header file(s). Key symbols: `[board.h:rp23xx_boardearlyinitialize]` Public declaration `rp23xx_boardearlyinitialize()`, `[board.h:rp23xx_boardinitialize]` Public declaration `rp23xx_boardinitialize()`.
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `pimoroni-pico-plus-2-w` (`arm/rp23xx`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 5 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
