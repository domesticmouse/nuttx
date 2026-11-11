# `at32f437-mini` Board Support Package (`boards/arm/at32/at32f437-mini`)

## Overview
Board Support Package (BSP) blueprint for `at32f437-mini` (`arm` / `at32`). Coordinates board initialization, headers, and tooling across `include, kernel, src, tool`. Includes build configurations: `adc`, `can_char`, `can_socket`, `eth`, `msc`, `nsh` (+6 more).

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `at32f437-mini` (`arm/at32`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:AT32_BOARD_XTAL]` Hardware/board configuration macros (`AT32_BOARD_XTAL`, `AT32_HSI_FREQUENCY`, `AT32_LSI_FREQUENCY`, `AT32_HSE_FREQUENCY`, `AT32_LSE_FREQUENCY`, `AT32_PLLCFG_PLLM` (+71 more)).
- [`kernel`](./kernel/README.md) - Protected-build userspace/kernel boundary module (`kernel`) for `at32f437-mini` (`arm/at32`), providing userspace initialization and syscall/gate hooks across 1 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[at32_userspace.c:g_userspace_data]` Module symbol `g_userspace_data`.
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `at32f437-mini` (`arm/at32`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 18 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[at32f437-mini.h:at32_bringup]` Public declaration `at32_bringup()`.
- [`tool`](./tool/README.md) - Board support component `tool` for `at32f437-mini` (`arm/at32`), containing 1 source/script file(s) (`mkromfs.sh`). Key symbols: `[mkromfs.sh]` Shell script entry point `mkromfs.sh`.
