# `ea3131` Board Support Package (`boards/arm/lpc31xx/ea3131`)

## Overview
Board Support Package (BSP) blueprint for `ea3131` (`arm` / `lpc31xx`). Coordinates board initialization, headers, and tooling across `include, locked, src, tools`. Includes build configurations: `nsh`, `pgnsh`, `usbserial`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `ea3131` (`arm/lpc31xx`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 2 header file(s). Key symbols: `[board.h:BOARD_FREQIN_FFAST]` Hardware/board configuration macros (`BOARD_FREQIN_FFAST`, `BOARD_HPLL0_FINSEL`, `BOARD_HPLL0_NDEC`, `BOARD_HPLL0_MDEC`, `BOARD_HPLL0_PDEC`, `BOARD_HPLL0_SELR` (+24 more)), `[board_memorymap.h:LPC31_SHADOWSPACE_VSECTION]` Hardware/board configuration macros (`LPC31_SHADOWSPACE_VSECTION`, `LPC31_INTSRAM_VSECTION`, `LPC31_INTSRAM0_VADDR`, `LPC31_INTSRAM1_VADDR`, `LPC31_INTSROM0_VSECTION`, `LPC31_APB01_VSECTION` (+18 more)).
- [`locked`](./locked/README.md) - Board support component `locked` for `ea3131` (`arm/lpc31xx`), containing 1 source/script file(s) (`mklocked.sh`). Key symbols: `[mklocked.sh]` Shell script entry point `mklocked.sh`.
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `ea3131` (`arm/lpc31xx`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 9 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[ea3131.h:lpc31_meminitialize]` Public declaration `lpc31_meminitialize()`.
- [`tools`](./tools/README.md) - Board support component `tools` for `ea3131` (`arm/lpc31xx`), containing 5 source/script file(s) (`crc32.c, lpchdr.c, lpchdr.h, mklpc.sh`). Key symbols: `[lpchdr.h:crc32part]` Public declaration `crc32part()`, `[lpchdr.h:crc32]` Public declaration `crc32()`.
