# `beagleplay` Board Support Package (`boards/arm64/am62x/beagleplay`)

## Overview
Board Support Package (BSP) blueprint for `beagleplay` (`arm64` / `am62x`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `i2c`, `nsh`, `ostest`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `beagleplay` (`arm64/am62x`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 2 header file(s). Key symbols: `[board.h:BOARD_UART_SCLK]` Hardware/board configuration macros (`BOARD_UART_SCLK`, `BOARD_ARCH_TIMER_FREQ`, `BOARD_LED_USR0`, `BOARD_LED_USR1`, `BOARD_LED_USR2`, `BOARD_LED_USR3` (+13 more)), `[board_memorymap.h:BEAGLEPLAY_DEVICEIO_BASE]` Hardware/board configuration macros (`BEAGLEPLAY_DEVICEIO_BASE`, `BEAGLEPLAY_DEVICEIO_SIZE`, `BEAGLEPLAY_DDR_BASE`, `BEAGLEPLAY_DDR_SIZE`, `BEAGLEPLAY_LOAD_ADDR`).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `beagleplay` (`arm64/am62x`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 4 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
