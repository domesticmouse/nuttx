# `nutiny-nuc120/src` Component (`boards/arm/nuc1xx/nutiny-nuc120/src`)

## Overview
Board-level C implementation (`src`) for `nutiny-nuc120` (`arm/nuc1xx`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 3 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[nutiny-nuc120.h:nuc_spidev_initialize]` Public declaration `nuc_spidev_initialize()`
- `[nutiny-nuc120.h:nuc_usbinitialize]` Public declaration `nuc_usbinitialize()`
- `[nutiny-nuc120.h:nuc_led_initialize]` Public declaration `nuc_led_initialize()`
- `[nutiny-nuc120.h:GPIO_LED]` Hardware/board configuration macros (`GPIO_LED`)
- `[nuc_boardinitialize.c:nuc_boardinitialize]` Public function `nuc_boardinitialize()`
- `[nuc_boardinitialize.c:board_late_initialize]` Public function `board_late_initialize()`
- `[nuc_led.c:nuc_led_initialize]` Public function `nuc_led_initialize()`
- `[nuc_led.c:board_autoled_on]` Public function `board_autoled_on()`
- `[nuc_led.c:board_autoled_off]` Public function `board_autoled_off()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_LEDS`, `CONFIG_NUC1XX_USBD`, `CONFIG_PWM`, `CONFIG_SENSORS_QENCODER`, `CONFIG_WATCHDOG`

## Side Effects
- `[nuc_boardinitialize.c:nuc_boardinitialize]` Initializes/registers kernel devices or filesystems (`nuc_led_initialize()`, `nuc_spidev_initialize()`)
- `[nuc_led.c:nuc_led_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh nutiny-nuc120:nsh && make`
