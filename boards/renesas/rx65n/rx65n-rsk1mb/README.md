# `rx65n-rsk1mb` Board Support Package (`boards/renesas/rx65n/rx65n-rsk1mb`)

## Overview
Board Support Package (BSP) blueprint for `rx65n-rsk1mb` (`renesas` / `rx65n`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `netnsh`, `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `rx65n-rsk1mb` (`renesas/rx65n`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 2 header file(s). Key symbols: `[board.h:RX_FCLK]` Hardware/board configuration macros (`RX_FCLK`, `RX_ICLK`, `RX_PCLKA`, `RX_PCLKB`, `RX_PCLKC`, `RX_PCLKD` (+13 more)), `[rx65n_gpio.h:sci_port_create]` Public declaration `sci_port_create()`.
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `rx65n-rsk1mb` (`renesas/rx65n`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 2 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[rx65n_gpio.c:led_port_create]` Public function `led_port_create()`.
