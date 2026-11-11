# `mirtoo/src` Component (`boards/mips/pic32mx/mirtoo/src`)

## Overview
Board-level C implementation (`src`) for `mirtoo` (`mips/pic32mx`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 5 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[mirtoo.h:pic32mx_spi2initialize]` Public declaration `pic32mx_spi2initialize()`
- `[mirtoo.h:pic32mx_led_initialize]` Public declaration `pic32mx_led_initialize()`
- `[pic32_adc.c:pic32mx_adcinitialize]` Public function `pic32mx_adcinitialize()`
- `[pic32_boot.c:pic32mx_boardinitialize]` Public function `pic32mx_boardinitialize()`
- `[pic32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[pic32_leds.c:board_userled_initialize]` Public function `board_userled_initialize()`
- `[pic32_leds.c:board_userled]` Public function `board_userled()`
- `[pic32_leds.c:board_userled_all]` Public function `board_userled_all()`
- `[pic32_leds.c:pic32mx_led_initialize]` Public function `pic32mx_led_initialize()`
- `[pic32_leds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[pic32_leds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[pic32_spi2.c:pic32mx_spi2initialize]` Public function `pic32mx_spi2initialize()`
- `[pic32_spi2.c:pic32mx_spi2select]` Public function `pic32mx_spi2select()`
- `[pic32_spi2.c:pic32mx_spi2status]` Public function `pic32mx_spi2status()`
- `[pic32_spi2.c:pic32mx_spi2cmddata]` Public function `pic32mx_spi2cmddata()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_PIC32MX_ADC`, `CONFIG_PIC32MX_SPI2`

## Side Effects
- `[pic32_boot.c:pic32mx_boardinitialize]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[pic32_boot.c:pic32mx_boardinitialize]` Configures or drives hardware GPIO pins
- `[pic32_boot.c:pic32mx_boardinitialize]` Initializes/registers kernel devices or filesystems (`nx_mount()`, `nxffs_initialize()`, `pic32mx_led_initialize()`, `pic32mx_spibus_initialize()`, `sst25_initialize()`)
- `[pic32_leds.c:board_userled_initialize]` Configures or drives hardware GPIO pins
- `[pic32_spi2.c:pic32mx_spi2initialize]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[pic32_spi2.c:pic32mx_spi2initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh mirtoo:nsh && make`
