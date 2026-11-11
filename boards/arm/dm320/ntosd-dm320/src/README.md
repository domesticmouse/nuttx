# `ntosd-dm320/src` Component (`boards/arm/dm320/ntosd-dm320/src`)

## Overview
Board-level C implementation (`src`) for `ntosd-dm320` (`arm/dm320`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 3 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[dm320_boardinit.c:board_late_initialize]` Public function `board_late_initialize()`
- `[dm320_leds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[dm320_leds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[dm320_leds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[dm320_network.c:dm9x_initialize]` Public function `dm9x_initialize()`
- `[dm320_network.c:arm_netinitialize]` Public function `arm_netinitialize()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_BOARD_LATE_INITIALIZE`

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh ntosd-dm320:nsh && make`
