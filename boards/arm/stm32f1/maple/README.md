# `maple` Board Support Package (`boards/arm/stm32f1/maple`)

## Overview
Board Support Package (BSP) blueprint for `maple` (`arm` / `stm32f1`). Coordinates board initialization, headers, and tooling across `include, src, tools`. Includes build configurations: `nsh`, `nx`, `usbnsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `maple` (`arm/stm32f1`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:STM32_BOARD_XTAL]` Hardware/board configuration macros (`STM32_BOARD_XTAL`, `STM32_CFGR_PLLSRC`, `STM32_CFGR_PLLXTPRE`, `STM32_CFGR_PLLMUL`, `STM32_PLL_FREQUENCY`, `STM32_SYSCLK_SW` (+48 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `maple` (`arm/stm32f1`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 6 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[CMakeLists.txt:board]` CMake build target source registration.
- [`tools`](./tools/README.md) - Board support component `tools` for `maple` (`arm/stm32f1`), containing 2 source/script file(s) (`dfu.sh, env.sh`). Key symbols: `[dfu.sh]` Shell script entry point `dfu.sh`, `[env.sh]` Shell script entry point `env.sh`.
