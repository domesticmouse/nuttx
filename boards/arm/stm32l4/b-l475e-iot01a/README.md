# `b-l475e-iot01a` Board Support Package (`boards/arm/stm32l4/b-l475e-iot01a`)

## Overview
Board Support Package (BSP) blueprint for `b-l475e-iot01a` (`arm` / `stm32l4`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`, `qemu`, `spirit-6lowpan`, `spirit-starhub`, `spirit-starpoint`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `b-l475e-iot01a` (`arm/stm32l4`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 2 header file(s). Key symbols: `[b-l475e-iot01a_clock.h:HSI_CLOCK_CONFIG]` Hardware/board configuration macros (`HSI_CLOCK_CONFIG`, `HSE_CLOCK_CONFIG`, `MSI_CLOCK_CONFIG`, `STM32_HSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_LSE_FREQUENCY` (+43 more)), `[board.h:BOARD_LED1]` Hardware/board configuration macros (`BOARD_LED1`, `BOARD_LED2`, `BOARD_NLEDS`, `BOARD_LED1_BIT`, `BOARD_LED2_BIT`, `LED_STARTED` (+42 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `b-l475e-iot01a` (`arm/stm32l4`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 8 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
