# `sama5d4-ek` Board Support Package (`boards/arm/sama5/sama5d4-ek`)

## Overview
Board Support Package (BSP) blueprint for `sama5d4-ek` (`arm` / `sama5`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `at25boot`, `bridge`, `dramboot`, `elf`, `ipv6`, `knsh` (+3 more).

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `sama5d4-ek` (`arm/sama5`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 6 header file(s). Key symbols: `[board.h:BOARD_MAINOSC_FREQUENCY]` Hardware/board configuration macros (`BOARD_MAINOSC_FREQUENCY`, `BOARD_SLOWCLK_FREQUENCY`, `BOARD_USER`, `BOARD_POWER`, `BOARD_NLEDS`, `BOARD_USER_BIT` (+37 more)), `[board_384mhz.h:BOARD_CKGR_MOR_MOSCXTST]` Hardware/board configuration macros (`BOARD_CKGR_MOR_MOSCXTST`, `BOARD_CKGR_PLLAR_COUNT`, `BOARD_CKGR_PLLAR_OUT`, `BOARD_CKGR_PLLAR_MUL`, `BOARD_PMC_MCKR_CSS`, `BOARD_PMC_MCKR_PRES` (+19 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `sama5d4-ek` (`arm/sama5`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 24 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[sama5d4-ek.h:sam_spidev_initialize]` Public declaration `sam_spidev_initialize()`.
