# `tms570ls31x-usb-kit/src` Component (`boards/arm/tms570/tms570ls31x-usb-kit/src`)

## Overview
Board-level C implementation (`src`) for `tms570ls31x-usb-kit` (`arm/tms570`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 8 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[tms570ls31x_usb_kit.h:tms570_bringup]` Public declaration `tms570_bringup()`
- `[tms570ls31x_usb_kit.h:tms570_mmcsd_initialize]` Public declaration `tms570_mmcsd_initialize()`
- `[tms570ls31x_usb_kit.h:GIO_LED_D11]` Hardware/board configuration macros (`GIO_LED_D11`, `GIO_BUTTON`, `IRQ_BUTTON`)
- `[tms570_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[tms570_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[tms570_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[tms570_bringup.c:tms570_bringup]` Public function `tms570_bringup()`
- `[tms570_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[tms570_buttons.c:board_buttons]` Public function `board_buttons()`
- `[tms570_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[tms570_initialize.c:tms570_board_initialize]` Public function `tms570_board_initialize()`
- `[tms570_initialize.c:board_late_initialize]` Public function `board_late_initialize()`
- `[tms570_sdmmc.c:tms570_spi1register]` Public function `tms570_spi1register()`
- `[tms570_sdmmc.c:tms570_mmcsd_initialize]` Public function `tms570_mmcsd_initialize()`
- `[tms570_spi.c:tms570_spidev_initialize]` Public function `tms570_spidev_initialize()`
- `[tms570_spi.c:tms570_spi1select]` Public function `tms570_spi1select()`
- `[tms570_spi.c:tms570_spi1status]` Public function `tms570_spi1status()`
- `[tms570_spi.c:tms570_spi4select]` Public function `tms570_spi4select()`
- `[tms570_spi.c:tms570_spi4status]` Public function `tms570_spi4status()`
- `[tms570_userleds.c:board_userled_initialize]` Public function `board_userled_initialize()`
- `[tms570_userleds.c:board_userled]` Public function `board_userled()`
- `[tms570_userleds.c:board_userled_all]` Public function `board_userled_all()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_MMCSD`
- `[tms570_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure
- `[tms570_sdmmc.c:#error]` Compile-time guard: `SD driver requires CONFIG_STM32_SPI1 to be enabled`
- `[tms570_sdmmc.c:#error]` Compile-time guard: `SD driver requires CONFIG_DISABLE_MOUNTPOINT to be disabled`

## Side Effects
- `[tms570_bringup.c:tms570_bringup]` Initializes/registers kernel devices or filesystems (`tms570_mmcsd_initialize()`, `tms570_spidev_initialize()`)
- `[tms570_buttons.c:board_button_initialize]` Modifies interrupt controller or critical-section state
- `[tms570_initialize.c:tms570_board_initialize]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[tms570_initialize.c:tms570_board_initialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`)
- `[tms570_sdmmc.c:tms570_spi1register]` Initializes/registers kernel devices or filesystems (`tms570_spibus_initialize()`)

## Verification
- Run: `./tools/configure.sh tms570ls31x-usb-kit:nsh && make`
