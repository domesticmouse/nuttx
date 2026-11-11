# `esp32c3-legacy-devkit-rust-1/include` Component (`boards/risc-v/esp32c3-legacy/esp32c3-legacy-devkit-rust-1/include`)

## Overview
Board-level public headers (`include`) for `esp32c3-legacy-devkit-rust-1` (`risc-v/esp32c3-legacy`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 2 header file(s).

## Interface
- `[board.h:NUM_BUTTONS]` Hardware/board configuration macros (`NUM_BUTTONS`, `LED_STARTED`, `LED_HEAPALLOCATE`, `LED_IRQSENABLED`, `LED_STACKCREATED`, `LED_INIRQ` (+7 more))
- `[board_memorymap.h:KIROM_START]` Hardware/board configuration macros (`KIROM_START`, `KIROM_SIZE`, `KDROM_START`, `KDROM_SIZE`, `KIRAM_START`, `KIRAM_SIZE` (+18 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh esp32c3-legacy-devkit-rust-1:nsh && make`
