# `common` Board Support Package (`boards/xtensa/esp32s3/common`)

## Overview
Board Support Package (BSP) blueprint for `common` (`xtensa` / `esp32s3`). Coordinates board initialization, headers, and tooling across `include, kernel, src`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `common` (`xtensa/esp32s3`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 11 header file(s). Key symbols: `[esp32s3_board_adc.h:board_adc_init]` Public declaration `board_adc_init()`, `[esp32s3_board_ledc.h:esp32s3_pwm_setup]` Public declaration `esp32s3_pwm_setup()`.
- [`kernel`](./kernel/README.md) - Protected-build userspace/kernel boundary module (`kernel`) for `common` (`xtensa/esp32s3`), providing userspace initialization and syscall/gate hooks across 1 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[esp32s3_userspace.c:g_userspace_data]` Module symbol `g_userspace_data`.
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `common` (`xtensa/esp32s3`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 22 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
