# `arduino-m0/src` Component (`boards/arm/samd2l2/arduino-m0/src`)

## Overview
Board-level C implementation (`src`) for `arduino-m0` (`arm/samd2l2`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 8 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[arduino_m0.h:sam_bringup]` Public declaration `sam_bringup()`
- `[arduino_m0.h:sam_adc_setup]` Public declaration `sam_adc_setup()`
- `[arduino_m0.h:sam_spidev_initialize]` Public declaration `sam_spidev_initialize()`
- `[arduino_m0.h:PORT_STATUS_LED]` Hardware/board configuration macros (`PORT_STATUS_LED`)
- `[sam_adc.c:sam_adc_setup]` Public function `sam_adc_setup()`
- `[sam_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[sam_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[sam_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[sam_boot.c:sam_boardinitialize]` Public function `sam_boardinitialize()`
- `[sam_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[sam_bringup.c:sam_bringup]` Public function `sam_bringup()`
- `[sam_spi.c:sam_spidev_initialize]` Public function `sam_spidev_initialize()`
- `[sam_spi.c:sam_spi0select]` Public function `sam_spi0select()`
- `[sam_spi.c:sam_spi1select]` Public function `sam_spi1select()`
- `[sam_spi.c:sam_spi2select]` Public function `sam_spi2select()`
- `[sam_spi.c:sam_spi3select]` Public function `sam_spi3select()`
- `[sam_spi.c:sam_spi4select]` Public function `sam_spi4select()`
- `[sam_spi.c:sam_spi5select]` Public function `sam_spi5select()`
- `[sam_spi.c:sam_spi0status]` Public function `sam_spi0status()`
- `[sam_spi.c:sam_spi1status]` Public function `sam_spi1status()`
- `[sam_spi.c:sam_spi2status]` Public function `sam_spi2status()`
- `[sam_spi.c:sam_spi3status]` Public function `sam_spi3status()`
- `[sam_spi.c:sam_spi4status]` Public function `sam_spi4status()`
- *(+12 additional symbols across 8 files)*

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_SAMD2L2_ADC`, `CONFIG_SAMD2L2_SERCOM0`, `CONFIG_USBDEV`
- `[sam_adc.c:sam_adc_setup]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[sam_adc.c:sam_adc_setup]` Initializes/registers kernel devices or filesystems (`adc_register()`)
- `[sam_boot.c:sam_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `sam_spidev_initialize()`)

## Verification
- Run: `./tools/configure.sh arduino-m0:nsh && make`
