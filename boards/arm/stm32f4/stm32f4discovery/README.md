# `stm32f4discovery` Board Support Package (`boards/arm/stm32f4/stm32f4discovery`)

## Overview
Board Support Package (BSP) blueprint for `stm32f4discovery` (`arm` / `stm32f4`). Coordinates board initialization, headers, and tooling across `include, kernel, src`. Includes build configurations: `adb`, `audio`, `brickmatch`, `canard`, `composite`, `cxx-oot-build` (+35 more).

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `stm32f4discovery` (`arm/stm32f4`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:board_kmatrix_diag]` Public declaration `board_kmatrix_diag()`, `[board.h:STM32_BOARD_XTAL]` Hardware/board configuration macros (`STM32_BOARD_XTAL`, `STM32_HSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_HSE_FREQUENCY`, `STM32_LSE_FREQUENCY`, `STM32_PLLCFG_PLLM` (+224 more)).
- [`kernel`](./kernel/README.md) - Protected-build userspace/kernel boundary module (`kernel`) for `stm32f4discovery` (`arm/stm32f4`), providing userspace initialization and syscall/gate hooks across 1 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `stm32f4discovery` (`arm/stm32f4`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 43 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
