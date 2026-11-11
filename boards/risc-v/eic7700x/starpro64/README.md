# `starpro64` Board Support Package (`boards/risc-v/eic7700x/starpro64`)

## Overview
Board Support Package (BSP) blueprint for `starpro64` (`risc-v` / `eic7700x`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `starpro64` (`risc-v/eic7700x`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 2 header file(s). Key symbols: `[board.h:eic7700x_boardinitialize]` Public declaration `eic7700x_boardinitialize()`, `[board_memorymap.h:KFLASH_START]` Hardware/board configuration macros (`KFLASH_START`, `KFLASH_SIZE`, `KSRAM_START`, `KSRAM_SIZE`, `KSRAM_END`, `PGPOOL_START` (+4 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `starpro64` (`risc-v/eic7700x`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 2 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[board_config.h:eic7700x_bringup]` Public declaration `eic7700x_bringup()`.
