# `common` Board Support Package (`boards/risc-v/esp32c3-legacy/common`)

## Overview
Board Support Package (BSP) blueprint for `common` (`risc-v` / `esp32c3-legacy`). Coordinates board initialization, headers, and tooling across `include, kernel, src`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `common` (`risc-v/esp32c3-legacy`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 14 header file(s). Key symbols: `[esp32c3_board_adc.h:board_adc_init]` Public declaration `board_adc_init()`, `[esp32c3_board_apds9960.h:board_apds9960_initialize]` Public declaration `board_apds9960_initialize()`.
- [`kernel`](./kernel/README.md) - Protected-build userspace/kernel boundary module (`kernel`) for `common` (`risc-v/esp32c3-legacy`), providing userspace initialization and syscall/gate hooks across 1 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[esp32c3_userspace.c:g_userspace_data]` Module symbol `g_userspace_data`.
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `common` (`risc-v/esp32c3-legacy`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 19 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
