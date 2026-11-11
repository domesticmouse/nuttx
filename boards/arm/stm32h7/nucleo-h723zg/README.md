# `nucleo-h723zg` Board Support Package (`boards/arm/stm32h7/nucleo-h723zg`)

## Overview
Board Support Package (BSP) blueprint for `nucleo-h723zg` (`arm` / `stm32h7`). Coordinates board initialization, headers, and tooling across `include, kernel, src`. Includes build configurations: `netnsh`, `nsh`, `oa_tc6`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `nucleo-h723zg` (`arm/stm32h7`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:STM32_BOARD_XTAL]` Hardware/board configuration macros (`STM32_BOARD_XTAL`, `STM32_HSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_HSE_FREQUENCY`, `STM32_LSE_FREQUENCY`, `STM32_BOARD_USEHSE` (+186 more)).
- [`kernel`](./kernel/README.md) - Protected-build userspace/kernel boundary module (`kernel`) for `nucleo-h723zg` (`arm/stm32h7`), providing userspace initialization and syscall/gate hooks across 1 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[stm32_userspace.c]` Translation unit `stm32_userspace.c`.
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `nucleo-h723zg` (`arm/stm32h7`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 14 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
