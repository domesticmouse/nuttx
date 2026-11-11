# `makerlisp` Board Support Package (`boards/z80/ez80/makerlisp`)

## Overview
Board Support Package (BSP) blueprint for `makerlisp` (`z80` / `ez80`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh_flash`, `nsh_ram`, `sdboot`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `makerlisp` (`z80/ez80`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:EZ80_SYS_CLK_FREQ]` Hardware/board configuration macros (`EZ80_SYS_CLK_FREQ`, `LED_STARTED`, `LED_HEAPALLOCATE`, `LED_IRQSENABLED`, `LED_STACKCREATED`, `LED_IDLE` (+4 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `makerlisp` (`z80/ez80`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 7 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[makerlisp.h:ez80_bringup]` Public declaration `ez80_bringup()`.
