# `tlsr8278adk80d` Board Support Package (`boards/arm/tlsr82/tlsr8278adk80d`)

## Overview
Board Support Package (BSP) blueprint for `tlsr8278adk80d` (`arm` / `tlsr82`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `tlsr8278adk80d` (`arm/tlsr82`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:BOARD_NGPIO]` Hardware/board configuration macros (`BOARD_NGPIO`, `BOARD_GPIO0_PIN`, `BOARD_GPIO0_TYPE`, `BOARD_GPIO1_PIN`, `BOARD_GPIO1_TYPE`, `BOARD_GPIO2_PIN` (+33 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `tlsr8278adk80d` (`arm/tlsr82`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 5 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[tlsr8278adk80d.h:tlsr8278_bringup]` Public declaration `tlsr8278_bringup()`.
