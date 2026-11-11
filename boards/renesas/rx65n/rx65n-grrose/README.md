# `rx65n-grrose` Board Support Package (`boards/renesas/rx65n/rx65n-grrose`)

## Overview
Board Support Package (BSP) blueprint for `rx65n-grrose` (`renesas` / `rx65n`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `ipv6`, `netnsh`, `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `rx65n-grrose` (`renesas/rx65n`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 2 header file(s). Key symbols: `[board.h:RX_FCLK]` Hardware/board configuration macros (`RX_FCLK`, `RX_ICLK`, `RX_PCLKA`, `RX_PCLKB`, `RX_PCLKC`, `RX_PCLKD` (+15 more)), `[rx65n_gpio.h:sci_port_create]` Public declaration `sci_port_create()`.
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `rx65n-grrose` (`renesas/rx65n`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 4 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[rx65n_grrose.h:rx65n_bringup]` Public declaration `rx65n_bringup()`.
