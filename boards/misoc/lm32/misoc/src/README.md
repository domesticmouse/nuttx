# `misoc/src` Component (`boards/misoc/lm32/misoc/src`)

## Overview
Board-level C implementation (`src`) for `misoc` (`misoc/lm32`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 2 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[misoc.h:lm32_spidev_initialize]` Public declaration `lm32_spidev_initialize()`
- `[misoc.h:lm32_led_initialize]` Public declaration `lm32_led_initialize()`
- `[lm32_boot.c:lm32_board_initialize]` Public function `lm32_board_initialize()`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh misoc:nsh && make`
