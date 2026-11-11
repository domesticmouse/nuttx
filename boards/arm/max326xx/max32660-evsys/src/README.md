# `max32660-evsys/src` Component (`boards/arm/max326xx/max32660-evsys/src`)

## Overview
Board-level C implementation (`src`) for `max32660-evsys` (`arm/max326xx`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 8 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[max32660-evsys.h:max326_bringup]` Public declaration `max326_bringup()`
- `[max32660-evsys.h:max326_spidev_initialize]` Public declaration `max326_spidev_initialize()`
- `[max32660-evsys.h:max326_mmcsd_initialize]` Public declaration `max326_mmcsd_initialize()`
- `[max32660-evsys.h:GPIO_LED]` Hardware/board configuration macros (`GPIO_LED`, `GPIO_BUTTON`, `BUTTON_IRQ`, `MICROSD_CS`)
- `[max326_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[max326_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[max326_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[max326_boot.c:max326_board_initialize]` Public function `max326_board_initialize()`
- `[max326_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[max326_bringup.c:max326_bringup]` Public function `max326_bringup()`
- `[max326_button.c:board_button_initialize]` Public function `board_button_initialize()`
- `[max326_button.c:board_buttons]` Public function `board_buttons()`
- `[max326_button.c:board_button_irq]` Public function `board_button_irq()`
- `[max326_mmcsd.c:max326_mmcsd_initialize]` Public function `max326_mmcsd_initialize()`
- `[max326_spi.c:max326_spidev_initialize]` Public function `max326_spidev_initialize()`
- `[max326_spi.c:max326_spi0select]` Public function `max326_spi0select()`
- `[max326_spi.c:max326_spi0status]` Public function `max326_spi0status()`
- `[max326_spi.c:max326_spi1select]` Public function `max326_spi1select()`
- `[max326_spi.c:max326_spi1status]` Public function `max326_spi1status()`
- `[max326_spi.c:max326_spi0cmddata]` Public function `max326_spi0cmddata()`
- `[max326_spi.c:max326_spi1cmddata]` Public function `max326_spi1cmddata()`
- `[max326_spi.c:max326_spi3cmddata]` Public function `max326_spi3cmddata()`
- `[max326_userleds.c:board_userled_initialize]` Public function `board_userled_initialize()`
- *(+2 additional symbols across 8 files)*

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_MAX326XX_HAVE_SPIM`, `CONFIG_MMCSD_SPI`
- `[max326_button.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure
- `[max326_mmcsd.c:#error]` Compile-time guard: `SD driver requires SPI master mode support`
- `[max326_mmcsd.c:#error]` Compile-time guard: `SD driver requires CONFIG_DISABLE_MOUNTPOINT to be disabled`
- `[max326_spi.c:max326_spidev_initialize]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[max326_boot.c:max326_board_initialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `max326_spidev_initialize()`)
- `[max326_bringup.c:max326_bringup]` Initializes/registers kernel devices or filesystems (`max326_mmcsd_initialize()`, `nx_mount()`)
- `[max326_button.c:board_button_initialize]` Modifies interrupt controller or critical-section state
- `[max326_mmcsd.c:max326_mmcsd_initialize]` Initializes/registers kernel devices or filesystems (`max326_spibus_initialize()`)

## Verification
- Run: `./tools/configure.sh max32660-evsys:nsh && make`
