# `efm32gg-stk3700` Board Support Package (`boards/arm/efm32/efm32gg-stk3700`)

## Overview
Board Support Package (BSP) blueprint for `efm32gg-stk3700` (`arm` / `efm32`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `efm32gg-stk3700` (`arm/efm32`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:board_format_sdcard]` Public declaration `board_format_sdcard()`, `[board.h:board_mount_sdcard]` Public declaration `board_mount_sdcard()`.
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `efm32gg-stk3700` (`arm/efm32`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 4 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[efm32gg-stk3700.h:GPIO_BC_EN]` Hardware/board configuration macros (`GPIO_BC_EN`, `GPIO_LED0`, `GPIO_LED1`).
