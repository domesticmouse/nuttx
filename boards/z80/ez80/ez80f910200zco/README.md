# `ez80f910200zco` Board Support Package (`boards/z80/ez80/ez80f910200zco`)

## Overview
Board Support Package (BSP) blueprint for `ez80f910200zco` (`z80` / `ez80`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `dhcpd`, `httpd`, `nettest`, `nsh`, `poll`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `ez80f910200zco` (`z80/ez80`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:EZ80_SYS_CLK_FREQ]` Hardware/board configuration macros (`EZ80_SYS_CLK_FREQ`, `LED_STARTED`, `LED_HEAPALLOCATE`, `LED_IRQSENABLED`, `LED_STACKCREATED`, `LED_IDLE` (+7 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `ez80f910200zco` (`z80/ez80`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 4 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[ez80f910200zco.h:EZ80_OFFCHIPFLASH]` Hardware/board configuration macros (`EZ80_OFFCHIPFLASH`, `EZ80_LEDGPIOCNTRL`, `EZ80_PLTFMSRAM`, `EZ80_MODULESRAM`, `EZ80_LEDANODE`, `EZ80_GPIOCNTRL` (+31 more)).
