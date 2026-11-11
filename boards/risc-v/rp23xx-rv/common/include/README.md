# `common/include` Component (`boards/risc-v/rp23xx-rv/common/include`)

## Overview
Board-level public headers (`include`) for `common` (`risc-v/rp23xx-rv`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 5 header file(s).

## Interface
- `[rp23xx_common_bringup.h:rp23xx_common_bringup]` Public declaration `rp23xx_common_bringup()`
- `[rp23xx_common_initialize.h:rp23xx_common_earlyinitialize]` Public declaration `rp23xx_common_earlyinitialize()`
- `[rp23xx_common_initialize.h:rp23xx_common_initialize]` Public declaration `rp23xx_common_initialize()`
- `[rp23xx_common_pico.h:rp23xx_dev_gpio_init]` Public declaration `rp23xx_dev_gpio_init()`
- `[rp23xx_pwmdev.h:rp23xx_pwmdev_initialize]` Public declaration `rp23xx_pwmdev_initialize()`
- `[rp23xx_uniqueid.h:rp23xx_uniqueid_initialize]` Public declaration `rp23xx_uniqueid_initialize()`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh sim:nsh && make`
