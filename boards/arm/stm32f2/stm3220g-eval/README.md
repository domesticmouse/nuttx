# `stm3220g-eval` Board Support Package (`boards/arm/stm32f2/stm3220g-eval`)

## Overview
Board Support Package (BSP) blueprint for `stm3220g-eval` (`arm` / `stm32f2`). Coordinates board initialization, headers, and tooling across `include, src, tools`. Includes build configurations: `dhcpd`, `nettest`, `nsh`, `nsh2`, `nxwm`, `telnetd`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `stm3220g-eval` (`arm/stm32f2`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:stm3220g_lcdclear]` Public declaration `stm3220g_lcdclear()`, `[board.h:STM32_BOARD_XTAL]` Hardware/board configuration macros (`STM32_BOARD_XTAL`, `STM32_HSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_HSE_FREQUENCY`, `STM32_LSE_FREQUENCY`, `STM32_PLLCFG_PLLM` (+151 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `stm3220g-eval` (`arm/stm32f2`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 17 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
- [`tools`](./tools/README.md) - Board support component `tools` for `stm3220g-eval` (`arm/stm32f2`), containing 1 source/script file(s) (`oocd.sh`). Key symbols: `[oocd.sh]` Shell script entry point `oocd.sh`.
