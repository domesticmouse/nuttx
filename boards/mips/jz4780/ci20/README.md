# `ci20` Board Support Package (`boards/mips/jz4780/ci20`)

## Overview
Board Support Package (BSP) blueprint for `ci20` (`mips` / `jz4780`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `jumbo`, `net`, `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `ci20` (`mips/jz4780`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:jz_usbhost_initialize]` Public declaration `jz_usbhost_initialize()`, `[board.h:BOARD_ETH_FLG]` Hardware/board configuration macros (`BOARD_ETH_FLG`, `POWER_LED`).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `ci20` (`mips/jz4780`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 5 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[ci20.h:jz4780_led_initialize]` Public declaration `jz4780_led_initialize()`.
