# `xmc4700-relax/src` Component (`boards/arm/xmc4/xmc4700-relax/src`)

## Overview
Board-level C implementation (`src`) for `xmc4700-relax` (`arm/xmc4`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 7 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[xmc4700-relax.h:xmc4_bringup]` Public declaration `xmc4_bringup()`
- `[xmc4700-relax.h:GPIO_LED1]` Hardware/board configuration macros (`GPIO_LED1`, `GPIO_LED2`, `GPIO_BUTTON1`, `GPIO_BUTTON2`, `GPIO_CS`)
- `[xmc4_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[xmc4_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[xmc4_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[xmc4_boot.c:xmc4_board_initialize]` Public function `xmc4_board_initialize()`
- `[xmc4_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[xmc4_bringup.c:xmc4_bringup]` Public function `xmc4_bringup()`
- `[xmc4_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[xmc4_buttons.c:board_buttons]` Public function `board_buttons()`
- `[xmc4_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[xmc4_spi.c:xmc4_spidev_initialize]` Public function `xmc4_spidev_initialize()`
- `[xmc4_spi.c:xmc4_spi0select]` Public function `xmc4_spi0select()`
- `[xmc4_spi.c:xmc4_spi1select]` Public function `xmc4_spi1select()`
- `[xmc4_spi.c:xmc4_spi2select]` Public function `xmc4_spi2select()`
- `[xmc4_spi.c:xmc4_spi3select]` Public function `xmc4_spi3select()`
- `[xmc4_spi.c:xmc4_spi4select]` Public function `xmc4_spi4select()`
- `[xmc4_spi.c:xmc4_spi0status]` Public function `xmc4_spi0status()`
- `[xmc4_spi.c:xmc4_spi1status]` Public function `xmc4_spi1status()`
- `[xmc4_spi.c:xmc4_spi2status]` Public function `xmc4_spi2status()`
- `[xmc4_spi.c:xmc4_spi3status]` Public function `xmc4_spi3status()`
- `[xmc4_spi.c:xmc4_spi4status]` Public function `xmc4_spi4status()`
- `[xmc4_spi.c:xmc4_spi0cmddata]` Public function `xmc4_spi0cmddata()`
- *(+7 additional symbols across 7 files)*

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_LEDS`, `CONFIG_INPUT_BUTTONS`, `CONFIG_XMC4_USCI_SPI`
- `[xmc4_bringup.c:xmc4_bringup]` Validates preconditions and returns `-ENODEV` on failure
- `[xmc4_buttons.c:board_button_initialize]` Validates preconditions and returns `-ENOSYS` on failure

## Side Effects
- `[xmc4_boot.c:xmc4_board_initialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `xmc4_spidev_initialize()`)
- `[xmc4_bringup.c:xmc4_bringup]` Initializes/registers kernel devices or filesystems (`spi_register()`, `userled_lower_initialize()`, `xmc4_spibus_initialize()`)

## Verification
- Run: `./tools/configure.sh xmc4700-relax:nsh && make`
