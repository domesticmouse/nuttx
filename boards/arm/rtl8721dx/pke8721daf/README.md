# `pke8721daf` Board Support Package (`boards/arm/rtl8721dx/pke8721daf`)

## Overview
Board Support Package (BSP) blueprint for `pke8721daf` (`arm` / `rtl8721dx`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `adc`, `gpio`, `i2c`, `nsh`, `pwm`, `rtc` (+4 more).

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `pke8721daf` (`arm/rtl8721dx`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h]` Board header declarations `board.h`.
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `pke8721daf` (`arm/rtl8721dx`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 12 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
