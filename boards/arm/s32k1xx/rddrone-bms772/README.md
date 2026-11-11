# `rddrone-bms772` Board Support Package (`boards/arm/s32k1xx/rddrone-bms772`)

## Overview
Board Support Package (BSP) blueprint for `rddrone-bms772` (`arm` / `s32k1xx`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `rddrone-bms772` (`arm/s32k1xx`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 2 header file(s). Key symbols: `[board.h:BOARD_XTAL_FREQUENCY]` Hardware/board configuration macros (`BOARD_XTAL_FREQUENCY`, `RDDRONE_BMS772_RUN_SYSCLK_FREQUENCY`, `RDDRONE_BMS772_VLPR_SYSCLK_FREQUENCY`, `BOARD_LED_R`, `BOARD_LED_G`, `BOARD_LED_B` (+30 more)), `[smbus_sbd.h:smbus_sbd_initialize]` Public declaration `smbus_sbd_initialize()`.
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `rddrone-bms772` (`arm/s32k1xx`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 16 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
