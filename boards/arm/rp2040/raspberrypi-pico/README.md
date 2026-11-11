# `raspberrypi-pico` Board Support Package (`boards/arm/rp2040/raspberrypi-pico`)

## Overview
Board Support Package (BSP) blueprint for `raspberrypi-pico` (`arm` / `rp2040`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `ads7046`, `audiopack`, `bmp280`, `composite`, `displaypack`, `enc28j60` (+14 more).

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `raspberrypi-pico` (`arm/rp2040`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 5 header file(s). Key symbols: `[board.h:rp2040_boardearlyinitialize]` Public declaration `rp2040_boardearlyinitialize()`, `[board.h:rp2040_boardinitialize]` Public declaration `rp2040_boardinitialize()`.
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `raspberrypi-pico` (`arm/rp2040`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 7 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
