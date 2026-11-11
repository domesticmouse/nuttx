# `ne64badge/src` Component (`boards/hc/m9s12/ne64badge/src`)

## Overview
Board-level C implementation (`src`) for `ne64badge` (`hc/m9s12`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 5 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[ne64badge.h:hcs12_spidev_initialize]` Public declaration `hcs12_spidev_initialize()`
- `[ne64badge.h:NE64BADGE_BUTTON1]` Hardware/board configuration macros (`NE64BADGE_BUTTON1`, `NE64BADGE_BUTTON2`, `NE64BADGE_LED1`, `NE64BADGE_LED2`)
- `[m9s12_boot.c:hcs12_boardinitialize]` Public function `hcs12_boardinitialize()`
- `[m9s12_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[m9s12_buttons.c:board_buttons]` Public function `board_buttons()`
- `[m9s12_leds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[m9s12_leds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[m9s12_leds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[m9s12_spi.c:hcs12_spidev_initialize]` Public function `hcs12_spidev_initialize()`
- `[m9s12_spi.c:hcs12_spiselect]` Public function `hcs12_spiselect()`
- `[m9s12_spi.c:hcs12_spistatus]` Public function `hcs12_spistatus()`

## Invariants
- None

## Side Effects
- `[m9s12_boot.c:hcs12_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `hcs12_spidev_initialize()`)
- `[m9s12_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[m9s12_leds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh ne64badge:ostest && make`
