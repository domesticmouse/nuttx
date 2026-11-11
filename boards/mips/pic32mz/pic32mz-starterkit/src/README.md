# `pic32mz-starterkit/src` Component (`boards/mips/pic32mz/pic32mz-starterkit/src`)

## Overview
Board-level C implementation (`src`) for `pic32mz-starterkit` (`mips/pic32mz`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 7 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[pic32mz-starterkit.h:pic32mz_spidev_initialize]` Public declaration `pic32mz_spidev_initialize()`
- `[pic32mz-starterkit.h:pic32mz_led_initialize]` Public declaration `pic32mz_led_initialize()`
- `[pic32mz-starterkit.h:pic32mz_bringup]` Public declaration `pic32mz_bringup()`
- `[pic32mz-starterkit.h:PIC32MZ_HAVE_MMCSD]` Hardware/board configuration macros (`PIC32MZ_HAVE_MMCSD`, `PIC32MZ_MMCSDSPIPORTNO`, `PIC32MZ_MMCSDSLOTNO`, `PIC32MZ_MMCSDMINOR`, `CONFIG_NSH_MMCSDSPIPORTNO`, `CONFIG_NSH_MMCSDSLOTNO` (+6 more))
- `[pic32mz_autoleds.c:pic32mz_led_initialize]` Public function `pic32mz_led_initialize()`
- `[pic32mz_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[pic32mz_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[pic32mz_boot.c:pic32mz_boardinitialize]` Public function `pic32mz_boardinitialize()`
- `[pic32mz_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[pic32mz_bringup.c:pic32mz_bringup]` Public function `pic32mz_bringup()`
- `[pic32mz_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[pic32mz_buttons.c:board_buttons]` Public function `board_buttons()`
- `[pic32mz_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[pic32mz_spi.c:pic32mz_spidev_initialize]` Public function `pic32mz_spidev_initialize()`
- `[pic32mz_spi.c:pic32mz_spi1select]` Public function `pic32mz_spi1select()`
- `[pic32mz_spi.c:pic32mz_spi1status]` Public function `pic32mz_spi1status()`
- `[pic32mz_spi.c:pic32mz_spi1cmddata]` Public function `pic32mz_spi1cmddata()`
- `[pic32mz_spi.c:pic32mz_spi2select]` Public function `pic32mz_spi2select()`
- `[pic32mz_spi.c:pic32mz_spi2status]` Public function `pic32mz_spi2status()`
- `[pic32mz_spi.c:pic32mz_spi2cmddata]` Public function `pic32mz_spi2cmddata()`
- `[pic32mz_spi.c:pic32mz_spi3select]` Public function `pic32mz_spi3select()`
- `[pic32mz_spi.c:pic32mz_spi3status]` Public function `pic32mz_spi3status()`
- `[pic32mz_spi.c:pic32mz_spi3cmddata]` Public function `pic32mz_spi3cmddata()`
- `[pic32mz_spi.c:pic32mz_spi4select]` Public function `pic32mz_spi4select()`
- *(+11 additional symbols across 7 files)*

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`
- `[pic32mz_bringup.c:pic32mz_bringup]` Validates preconditions and returns `-ENODEV` on failure
- `[pic32mz_buttons.c:board_button_initialize]` Validates preconditions and returns `-ENOSYS` on failure

## Side Effects
- `[pic32mz_autoleds.c:pic32mz_led_initialize]` Configures or drives hardware GPIO pins
- `[pic32mz_boot.c:pic32mz_boardinitialize]` Initializes/registers kernel devices or filesystems (`pic32mz_led_initialize()`, `pic32mz_spidev_initialize()`)
- `[pic32mz_bringup.c:pic32mz_bringup]` Initializes/registers kernel devices or filesystems (`pic32mz_spibus_initialize()`)
- `[pic32mz_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[pic32mz_userleds.c:board_userled_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh pic32mz-starterkit:nsh && make`
