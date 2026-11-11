# `maix-bit/include` Component (`boards/risc-v/k210/maix-bit/include`)

## Overview
Board-level public headers (`include`) for `maix-bit` (`risc-v/k210`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:k210_boardinitialize]` Public declaration `k210_boardinitialize()`
- `[board.h:BOARD_LED_PAD]` Hardware/board configuration macros (`BOARD_LED_PAD`, `BOARD_LED_IO_FUNC`, `BOARD_LED_IO`, `LED_STARTED`, `LED_HEAPALLOCATE`, `LED_IRQSENABLED` (+10 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh maix-bit:nsh && make`
