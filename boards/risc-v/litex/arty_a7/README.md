# `arty_a7` Board Support Package (`boards/risc-v/litex/arty_a7`)

## Overview
Board Support Package (BSP) blueprint for `arty_a7` (`risc-v` / `litex`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `knsh`, `knsh-tickless`, `netnsh`, `nsh`, `nsh-tickless`, `nsh-vexii` (+2 more).

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `arty_a7` (`risc-v/litex`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 4 header file(s). Key symbols: `[board.h:litex_boardinitialize]` Public declaration `litex_boardinitialize()`, `[board_memorymap.h:KFLASH_START]` Hardware/board configuration macros (`KFLASH_START`, `KFLASH_SIZE`, `KSRAM_START`, `KSRAM_SIZE`, `KSRAM_END`, `PGPOOL_START` (+6 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `arty_a7` (`risc-v/litex`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 9 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[arty_a7.h:litex_bringup]` Public declaration `litex_bringup()`.
