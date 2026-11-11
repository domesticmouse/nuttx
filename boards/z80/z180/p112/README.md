# `p112` Board Support Package (`boards/z80/z180/p112`)

## Overview
Board Support Package (BSP) blueprint for `p112` (`z80` / `z180`). Coordinates board initialization, headers, and tooling across `include`. Includes build configurations: `ostest`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `p112` (`z80/z180`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:Z180_BOARD_XTAL]` Hardware/board configuration macros (`Z180_BOARD_XTAL`, `Z180_SYSCLOCK`).
