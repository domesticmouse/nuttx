# `twr-k60n512/src` Component (`boards/arm/kinetis/twr-k60n512/src`)

## Overview
Board-level C implementation (`src`) for `twr-k60n512` (`arm/kinetis`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 7 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[twr-k60n512.h:kinetis_spidev_initialize]` Public declaration `kinetis_spidev_initialize()`
- `[twr-k60n512.h:kinetis_usbinitialize]` Public declaration `kinetis_usbinitialize()`
- `[twr-k60n512.h:GPIO_SD_CARDDETECT]` Hardware/board configuration macros (`GPIO_SD_CARDDETECT`, `GPIO_SD_WRPROTECT`, `GPIO_SW1`, `GPIO_SW2`, `GPIO_LED1`, `GPIO_LED2` (+2 more))
- `[k60_boot.c:kinetis_boardinitialize]` Public function `kinetis_boardinitialize()`
- `[k60_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[k60_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[k60_buttons.c:board_buttons]` Public function `board_buttons()`
- `[k60_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[k60_leds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[k60_leds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[k60_leds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[k60_spi.c:kinetis_spidev_initialize]` Public function `kinetis_spidev_initialize()`
- `[k60_spi.c:kinetis_spi0select]` Public function `kinetis_spi0select()`
- `[k60_spi.c:kinetis_spi0status]` Public function `kinetis_spi0status()`
- `[k60_spi.c:kinetis_spi1select]` Public function `kinetis_spi1select()`
- `[k60_spi.c:kinetis_spi1status]` Public function `kinetis_spi1status()`
- `[k60_spi.c:kinetis_spi2select]` Public function `kinetis_spi2select()`
- `[k60_spi.c:kinetis_spi2status]` Public function `kinetis_spi2status()`
- `[k60_usbdev.c:kinetis_usbinitialize]` Public function `kinetis_usbinitialize()`
- `[k60_usbdev.c:kinetis_usbpullup]` Public function `kinetis_usbpullup()`
- `[k60_usbdev.c:kinetis_usbsuspend]` Public function `kinetis_usbsuspend()`
- `[k60_usbmsc.c:board_usbmsc_initialize]` Public function `board_usbmsc_initialize()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_USBDEV`, `CONFIG_USBMSC`
- `[k60_boot.c:#error]` Compile-time guard: `Only one MMC/SD slot, slot 0`
- `[k60_boot.c:#error]` Compile-time guard: `Unrecognized Kinetis board`
- `[k60_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure
- `[k60_usbmsc.c:#error]` Compile-time guard: `Unrecognized Kinetis board`

## Side Effects
- `[k60_boot.c:kinetis_boardinitialize]` Configures or drives hardware GPIO pins
- `[k60_boot.c:kinetis_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `kinetis_spidev_initialize()`, `sdhc_initialize()`)
- `[k60_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[k60_leds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh twr-k60n512:nsh && make`
