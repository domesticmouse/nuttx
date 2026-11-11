# `misoc` Board Support Package (`boards/misoc/lm32/misoc`)

## Overview
Board Support Package (BSP) blueprint for `misoc` (`misoc` / `lm32`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `hello`, `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `misoc` (`misoc/lm32`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:BOARD_XTAL_FREQ]` Hardware/board configuration macros (`BOARD_XTAL_FREQ`, `BOARD_CPU_CLOCK`, `BOARD_TOSCK_CLOCK`, `LED_STARTED`, `LED_HEAPALLOCATE`, `LED_IRQSENABLED` (+5 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `misoc` (`misoc/lm32`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 2 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[misoc.h:lm32_spidev_initialize]` Public declaration `lm32_spidev_initialize()`.
