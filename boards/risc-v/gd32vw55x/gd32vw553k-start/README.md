# `gd32vw553k-start` Board Support Package (`boards/risc-v/gd32vw55x/gd32vw553k-start`)

## Overview
Board Support Package (BSP) blueprint for `gd32vw553k-start` (`risc-v` / `gd32vw55x`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `adc`, `ble`, `littlefs`, `nsh`, `ostest`, `periph` (+6 more).

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `gd32vw553k-start` (`risc-v/gd32vw55x`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:BOARD_HXTAL_FREQUENCY]` Hardware/board configuration macros (`BOARD_HXTAL_FREQUENCY`, `BOARD_IRC32K_FREQUENCY`, `BOARD_SYSCLK_FREQUENCY`, `BOARD_UART2_TX_GPIO`, `BOARD_UART2_TX_PIN`, `BOARD_UART2_TX_AF` (+43 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `gd32vw553k-start` (`risc-v/gd32vw55x`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 8 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[gd32vw553k-start.h:gd32_bringup]` Public declaration `gd32_bringup()`.
