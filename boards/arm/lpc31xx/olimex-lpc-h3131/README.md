# `olimex-lpc-h3131` Board Support Package (`boards/arm/lpc31xx/olimex-lpc-h3131`)

## Overview
Board Support Package (BSP) blueprint for `olimex-lpc-h3131` (`arm` / `lpc31xx`). Coordinates board initialization, headers, and tooling across `include, src, tools`. Includes build configurations: `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `olimex-lpc-h3131` (`arm/lpc31xx`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 2 header file(s). Key symbols: `[board.h:lpc31_setup_overcurrent]` Public declaration `lpc31_setup_overcurrent()`, `[board.h:BOARD_FREQIN_FFAST]` Hardware/board configuration macros (`BOARD_FREQIN_FFAST`, `BOARD_HPLL0_FINSEL`, `BOARD_HPLL0_NDEC`, `BOARD_HPLL0_MDEC`, `BOARD_HPLL0_PDEC`, `BOARD_HPLL0_SELR` (+29 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `olimex-lpc-h3131` (`arm/lpc31xx`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 8 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[lpc_h3131.h:lpc31_meminitialize]` Public declaration `lpc31_meminitialize()`.
- [`tools`](./tools/README.md) - Board support component `tools` for `olimex-lpc-h3131` (`arm/lpc31xx`), containing 5 source/script file(s) (`crc32.c, lpchdr.c, lpchdr.h, mklpc.sh`). Key symbols: `[lpchdr.h:crc32part]` Public declaration `crc32part()`, `[lpchdr.h:crc32]` Public declaration `crc32()`.
