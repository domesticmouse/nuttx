# `ox64/src` Component (`boards/risc-v/bl808/ox64/src`)

## Overview
Board-level C implementation (`src`) for `ox64` (`risc-v/bl808`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 3 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[bl808_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[bl808_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[bl808_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[bl808_boardinit.c:board_late_initialize]` Public function `board_late_initialize()`
- `[bl808_userleds.c:board_userled_initialize]` Public function `board_userled_initialize()`
- `[bl808_userleds.c:board_userled]` Public function `board_userled()`
- `[bl808_userleds.c:board_userled_all]` Public function `board_userled_all()`

## Invariants
- `[bl808_autoleds.c:DEBUGASSERT]` Requires `ret == OK`
- `[bl808_userleds.c:DEBUGASSERT]` Requires `ret == OK`

## Side Effects
- `[bl808_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[bl808_boardinit.c:board_late_initialize]` Initializes/registers kernel devices or filesystems (`bl808_i2cbus_initialize()`, `bl808_spibus_initialize()`, `i2c_register()`, `spi_register()`, `userled_lower_initialize()`)
- `[bl808_userleds.c:board_userled_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh ox64:nsh && make`
