# `xmc4500-relax/src` Component (`boards/arm/xmc4/xmc4500-relax/src`)

## Overview
Board-level C implementation (`src`) for `xmc4500-relax` (`arm/xmc4`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 8 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[xmc4500-relax.h:xmc4_bringup]` Public declaration `xmc4_bringup()`
- `[xmc4500-relax.h:GPIO_LED1]` Hardware/board configuration macros (`GPIO_LED1`, `GPIO_LED2`, `GPIO_BUTTON1`, `GPIO_BUTTON2`, `GPIO_CS_MAX6675`)
- `[xmc4_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[xmc4_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[xmc4_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[xmc4_boot.c:xmc4_board_initialize]` Public function `xmc4_board_initialize()`
- `[xmc4_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[xmc4_bringup.c:xmc4_bringup]` Public function `xmc4_bringup()`
- `[xmc4_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[xmc4_buttons.c:board_buttons]` Public function `board_buttons()`
- `[xmc4_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[xmc4_max6675.c:xmc4_max6675initialize]` Public function `xmc4_max6675initialize()`
- `[xmc4_spi.c:xmc4_spidev_initialize]` Public function `xmc4_spidev_initialize()`
- `[xmc4_spi.c:xmc4_spi0select]` Public function `xmc4_spi0select()`
- `[xmc4_spi.c:xmc4_spi1select]` Public function `xmc4_spi1select()`
- `[xmc4_spi.c:xmc4_spi2select]` Public function `xmc4_spi2select()`
- `[xmc4_spi.c:xmc4_spi3select]` Public function `xmc4_spi3select()`
- `[xmc4_spi.c:xmc4_spi0status]` Public function `xmc4_spi0status()`
- `[xmc4_spi.c:xmc4_spi1status]` Public function `xmc4_spi1status()`
- `[xmc4_spi.c:xmc4_spi2status]` Public function `xmc4_spi2status()`
- `[xmc4_spi.c:xmc4_spi3status]` Public function `xmc4_spi3status()`
- `[xmc4_spi.c:xmc4_spi0cmddata]` Public function `xmc4_spi0cmddata()`
- `[xmc4_spi.c:xmc4_spi1cmddata]` Public function `xmc4_spi1cmddata()`
- *(+5 additional symbols across 8 files)*

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_LEDS`, `CONFIG_INPUT_BUTTONS`, `CONFIG_SENSORS_MAX6675`, `CONFIG_XMC4_USCI_SPI`
- `[xmc4_buttons.c:board_button_initialize]` Validates preconditions and returns `-ENOSYS` on failure
- `[xmc4_max6675.c:xmc4_max6675initialize]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[xmc4_boot.c:xmc4_board_initialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `xmc4_spidev_initialize()`)
- `[xmc4_max6675.c:xmc4_max6675initialize]` Initializes/registers kernel devices or filesystems (`max6675_register()`, `xmc4_spibus_initialize()`)

## Verification
- Run: `./tools/configure.sh xmc4500-relax:nsh && make`
