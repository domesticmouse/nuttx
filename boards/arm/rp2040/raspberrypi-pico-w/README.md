# `raspberrypi-pico-w` Board Support Package (`boards/arm/rp2040/raspberrypi-pico-w`)

## Overview
Board Support Package (BSP) blueprint for `raspberrypi-pico-w` (`arm` / `rp2040`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `audiopack`, `composite`, `displaypack`, `enc28j60`, `lcd1602`, `nsh` (+11 more).

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `raspberrypi-pico-w` (`arm/rp2040`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 6 header file(s). Key symbols: `[board.h:rp2040_boardearlyinitialize]` Public declaration `rp2040_boardearlyinitialize()`, `[board.h:rp2040_boardinitialize]` Public declaration `rp2040_boardinitialize()`.
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `raspberrypi-pico-w` (`arm/rp2040`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 4 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
