# `waveshare-rp2040-lcd-1.28` Board Support Package (`boards/arm/rp2040/waveshare-rp2040-lcd-1.28`)

## Overview
Board Support Package (BSP) blueprint for `waveshare-rp2040-lcd-1.28` (`arm` / `rp2040`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `composite`, `fastboot_usb`, `fb`, `lvgl`, `nsh`, `nsh-flash` (+5 more).

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `waveshare-rp2040-lcd-1.28` (`arm/rp2040`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 5 header file(s). Key symbols: `[board.h:rp2040_boardearlyinitialize]` Public declaration `rp2040_boardearlyinitialize()`, `[board.h:rp2040_boardinitialize]` Public declaration `rp2040_boardinitialize()`.
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `waveshare-rp2040-lcd-1.28` (`arm/rp2040`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 4 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
