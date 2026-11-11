# `common` Board Support Package (`boards/xtensa/esp32/common`)

## Overview
Board Support Package (BSP) blueprint for `common` (`xtensa` / `esp32`). Coordinates board initialization, headers, and tooling across `include, kernel, src`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `common` (`xtensa/esp32`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 30 header file(s). Key symbols: `[board_qencoder.h:board_qencoder_initialize]` Public declaration `board_qencoder_initialize()`, `[esp32_backlight.h:esp32_set_backlight]` Public declaration `esp32_set_backlight()`.
- [`kernel`](./kernel/README.md) - Protected-build userspace/kernel boundary module (`kernel`) for `common` (`xtensa/esp32`), providing userspace initialization and syscall/gate hooks across 1 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[esp32_userspace.c:g_userspace_data]` Module symbol `g_userspace_data`.
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `common` (`xtensa/esp32`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 39 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
