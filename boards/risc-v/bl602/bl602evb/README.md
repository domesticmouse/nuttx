# `bl602evb` Board Support Package (`boards/risc-v/bl602/bl602evb`)

## Overview
Board Support Package (BSP) blueprint for `bl602evb` (`risc-v` / `bl602`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `dma`, `elf`, `fpu`, `gpio`, `i2c`, `nsh` (+4 more).

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `bl602evb` (`risc-v/bl602`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:bl602_boardinitialize]` Public declaration `bl602_boardinitialize()`, `[board.h:BOARD_NGPIOIN]` Hardware/board configuration macros (`BOARD_NGPIOIN`, `BOARD_NGPIOOUT`, `BOARD_NGPIOINT`, `BOARD_GPIO_IN1`, `BOARD_GPIO_OUT1`, `BOARD_GPIO_INT1` (+15 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `bl602evb` (`risc-v/bl602`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 6 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[bl602evb.h:bl602_bringup]` Public declaration `bl602_bringup()`.
