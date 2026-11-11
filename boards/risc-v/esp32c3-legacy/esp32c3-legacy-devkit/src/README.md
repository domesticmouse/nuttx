# `esp32c3-legacy-devkit/src` Component (`boards/risc-v/esp32c3-legacy/esp32c3-legacy-devkit/src`)

## Overview
Board-level C implementation (`src`) for `esp32c3-legacy-devkit` (`risc-v/esp32c3-legacy`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 7 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[esp32c3-legacy-devkit.h:esp32c3_bringup]` Public declaration `esp32c3_bringup()`
- `[esp32c3-legacy-devkit.h:esp32c3_gpio_init]` Public declaration `esp32c3_gpio_init()`
- `[esp32c3-legacy-devkit.h:TIMER0]` Hardware/board configuration macros (`TIMER0`, `TIMER1`, `ONESHOT_TIMER`, `ONESHOT_RESOLUTION_US`)
- `[esp32c3_boot.c:esp32c3_board_initialize]` Public function `esp32c3_board_initialize()`
- `[esp32c3_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[esp32c3_bringup.c:esp32c3_bringup]` Public function `esp32c3_bringup()`
- `[esp32c3_gpio.c:esp32c3_gpio_init]` Public function `esp32c3_gpio_init()`
- `[esp32c3_ioctl.c:board_ioctl]` Public function `board_ioctl()`
- `[esp32c3_reset.c:board_reset]` Public function `board_reset()`
- `[esp32c3_uid.c:board_uniqueid]` Public function `board_uniqueid()`

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_BOARDCTL_IOCTL`, `CONFIG_BOARDCTL_RESET`, `CONFIG_BOARDCTL_UNIQUEID`, `CONFIG_DEV_GPIO`, `CONFIG_ETC_ROMFS`
- `[esp32c3_gpio.c:DEBUGASSERT]` Requires `esp32c3gpio != NULL && value != NULL`
- `[esp32c3_gpio.c:DEBUGASSERT]` Requires `esp32c3gpio->id < BOARD_NGPIOOUT`
- `[esp32c3_gpio.c:DEBUGASSERT]` Requires `esp32c3gpio != NULL`
- `[esp32c3_gpio.c:#error]` Compile-time guard: `NGPIOINT is > 0 and GPIO interrupts aren't enabled`
- `[esp32c3_ioctl.c:board_ioctl]` Validates preconditions and returns `-ENOTTY` on failure
- `[esp32c3_uid.c:board_uniqueid]` Validates preconditions and returns `-EINVAL` on failure

## Side Effects
- `[esp32c3_boot.c:esp32c3_board_initialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`)
- `[esp32c3_bringup.c:esp32c3_bringup]` Initializes/registers kernel devices or filesystems (`board_bmp180_initialize()`, `board_lcd_initialize()`, `board_mpu60x0_initialize()`, `board_spidev_initialize()`, `board_spislavedev_initialize()`)
- `[esp32c3_gpio.c:esp32c3_gpio_init]` Configures or drives hardware GPIO pins
- `[esp32c3_gpio.c:esp32c3_gpio_init]` Initializes/registers kernel devices or filesystems (`gpio_pin_register()`)
- `[esp32c3_gpio.c:esp32c3_gpio_init]` Modifies interrupt controller or critical-section state

## Verification
- Run: `./tools/configure.sh esp32c3-legacy-devkit:nsh && make`
