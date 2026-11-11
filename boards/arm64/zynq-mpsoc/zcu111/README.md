# `zcu111` Board Support Package (`boards/arm64/zynq-mpsoc/zcu111`)

## Overview
Board Support Package (BSP) blueprint for `zcu111` (`arm64` / `zynq-mpsoc`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `jtag`, `netjtag`, `netnsh`, `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `zcu111` (`arm64/zynq-mpsoc`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:BOARD_LED1]` Hardware/board configuration macros (`BOARD_LED1`, `BOARD_NLEDS`, `BOARD_LED1_BIT`, `LED_STARTED`, `LED_HEAPALLOCATE`, `LED_IRQSENABLED` (+10 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `zcu111` (`arm64/zynq-mpsoc`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 7 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[zcu111.h:zcu111_bringup]` Public declaration `zcu111_bringup()`.
