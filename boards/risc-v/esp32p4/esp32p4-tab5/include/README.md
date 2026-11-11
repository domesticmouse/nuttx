# `esp32p4-tab5/include` Component (`boards/risc-v/esp32p4/esp32p4-tab5/include`)

## Overview
Board-level public headers (`include`) for `esp32p4-tab5` (`risc-v/esp32p4`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:TAB5_GPIO_PC_TX]` Hardware/board configuration macros (`TAB5_GPIO_PC_TX`, `TAB5_GPIO_PC_RX`, `TAB5_GPIO_I2C0_SDA`, `TAB5_GPIO_I2C0_SCL`, `TAB5_GPIO_GROVE_SDA`, `TAB5_GPIO_GROVE_SCL` (+57 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh esp32p4-tab5:nsh && make`
