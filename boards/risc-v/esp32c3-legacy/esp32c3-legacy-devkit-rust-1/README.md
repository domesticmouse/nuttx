# `esp32c3-legacy-devkit-rust-1` Board Support Package (`boards/risc-v/esp32c3-legacy/esp32c3-legacy-devkit-rust-1`)

## Overview
Board Support Package (BSP) blueprint for `esp32c3-legacy-devkit-rust-1` (`risc-v` / `esp32c3-legacy`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `brickmatch`, `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `esp32c3-legacy-devkit-rust-1` (`risc-v/esp32c3-legacy`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 2 header file(s). Key symbols: `[board.h:NUM_BUTTONS]` Hardware/board configuration macros (`NUM_BUTTONS`, `LED_STARTED`, `LED_HEAPALLOCATE`, `LED_IRQSENABLED`, `LED_STACKCREATED`, `LED_INIRQ` (+7 more)), `[board_memorymap.h:KIROM_START]` Hardware/board configuration macros (`KIROM_START`, `KIROM_SIZE`, `KDROM_START`, `KDROM_SIZE`, `KIRAM_START`, `KIRAM_SIZE` (+18 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `esp32c3-legacy-devkit-rust-1` (`risc-v/esp32c3-legacy`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 6 source file(s). Key symbols: `[Make.defs:CSRCS]` Registered build sources in `Make.defs`, `[esp32c3-legacy-devkit-rust-1.h:esp32c3_bringup]` Public declaration `esp32c3_bringup()`.
