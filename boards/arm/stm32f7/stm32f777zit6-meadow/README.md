# `stm32f777zit6-meadow` Board Support Package (`boards/arm/stm32f7/stm32f777zit6-meadow`)

## Overview
Board Support Package (BSP) blueprint for `stm32f777zit6-meadow` (`arm` / `stm32f7`). Coordinates board initialization, headers, and tooling across `include, kernel, src`. Includes build configurations: `dualcdcacm`, `f7corecomp`, `i2s`, `meadow_os`, `nsh`, `projectlab` (+2 more).

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `stm32f777zit6-meadow` (`arm/stm32f7`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:STM32_BOARD_XTAL]` Hardware/board configuration macros (`STM32_BOARD_XTAL`, `STM32_HSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_HSE_FREQUENCY`, `STM32_LSE_FREQUENCY`, `STM32_PLLCFG_PLLM` (+190 more)).
- [`kernel`](./kernel/README.md) - Protected-build userspace/kernel boundary module (`kernel`) for `stm32f777zit6-meadow` (`arm/stm32f7`), providing userspace initialization and syscall/gate hooks across 1 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[stm32_userspace.c:g_userspace_data]` Module symbol `g_userspace_data`.
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `stm32f777zit6-meadow` (`arm/stm32f7`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 14 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
