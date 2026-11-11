# `raspberrypi-4b` Board Support Package (`boards/arm64/bcm2711/raspberrypi-4b`)

## Overview
Board Support Package (BSP) blueprint for `raspberrypi-4b` (`arm64` / `bcm2711`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `audio_tone`, `baromonitor`, `bmp280`, `cgol`, `coremark`, `fb` (+8 more).

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `raspberrypi-4b` (`arm64/bcm2711`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:STATUS_LED]` Hardware/board configuration macros (`STATUS_LED`, `POWER_LED`, `LED_STARTED`, `LED_HEAPALLOCATE`, `LED_IRQSENABLED`, `LED_STACKCREATED` (+8 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `raspberrypi-4b` (`arm64/bcm2711`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 9 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
