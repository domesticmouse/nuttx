# `phy6222` Board Support Package (`boards/arm/phy62xx/phy6222`)

## Overview
Board Support Package (BSP) blueprint for `phy6222` (`arm` / `phy62xx`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`, `phy_sbp`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `phy6222` (`arm/phy62xx`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:HCLK_FREQUENCY]` Hardware/board configuration macros (`HCLK_FREQUENCY`).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `phy6222` (`arm/phy62xx`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 7 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[phy6222.h:phy62xx_bringup]` Public declaration `phy62xx_bringup()`.
