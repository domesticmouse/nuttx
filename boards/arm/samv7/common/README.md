# `common` Board Support Package (`boards/arm/samv7/common`)

## Overview
Board Support Package (BSP) blueprint for `common` (`arm` / `samv7`). Coordinates board initialization, headers, and tooling across `include, src, tools`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `common` (`arm/samv7`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 6 header file(s). Key symbols: `[board_gpio_enc.h:sam_gpio_enc_init]` Public declaration `sam_gpio_enc_init()`, `[board_hsmci.h:sam_hsmci_initialize]` Public declaration `sam_hsmci_initialize()`.
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `common` (`arm/samv7`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 7 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[sam_automount.c:sam_automount_initialize]` Public function `sam_automount_initialize()`.
- [`tools`](./tools/README.md) - Board support component `tools` for `common` (`arm/samv7`), containing 1 source/script file(s) (`oocd.sh`). Key symbols: `[oocd.sh]` Shell script entry point `oocd.sh`.
