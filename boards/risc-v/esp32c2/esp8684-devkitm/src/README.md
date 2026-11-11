# `esp8684-devkitm/src` Component (`boards/risc-v/esp32c2/esp8684-devkitm/src`)

## Overview
Board-level C implementation (`src`) for `esp8684-devkitm` (`risc-v/esp32c2`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 6 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[esp8684-devkitm.h:esp_bringup]` Public declaration `esp_bringup()`
- `[esp8684-devkitm.h:esp_gpio_init]` Public declaration `esp_gpio_init()`
- `[esp32c2_boot.c:esp_board_initialize]` Public function `esp_board_initialize()`
- `[esp32c2_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[esp32c2_bringup.c:esp_bringup]` Public function `esp_bringup()`
- `[esp32c2_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[esp32c2_buttons.c:board_buttons]` Public function `board_buttons()`
- `[esp32c2_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[esp32c2_gpio.c:esp_gpio_init]` Public function `esp_gpio_init()`
- `[esp32c2_reset.c:board_reset]` Public function `board_reset()`

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_BUTTONS`, `CONFIG_BOARDCTL_RESET`, `CONFIG_DEV_GPIO`
- `[esp32c2_gpio.c:DEBUGASSERT]` Requires `espgpio != NULL && value != NULL`
- `[esp32c2_gpio.c:DEBUGASSERT]` Requires `espgpio->id < BOARD_NGPIOOUT`
- `[esp32c2_gpio.c:DEBUGASSERT]` Requires `espgpio != NULL`
- `[esp32c2_gpio.c:#error]` Compile-time guard: `NGPIOINT is > 0 and GPIO interrupts aren't enabled`

## Side Effects
- `[esp32c2_bringup.c:esp_bringup]` Initializes/registers kernel devices or filesystems (`board_bmp180_initialize()`, `board_spidev_initialize()`, `board_spislavedev_initialize()`, `btn_lower_initialize()`, `esp_ble_initialize()`)
- `[esp32c2_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[esp32c2_gpio.c:esp_gpio_init]` Configures or drives hardware GPIO pins
- `[esp32c2_gpio.c:esp_gpio_init]` Initializes/registers kernel devices or filesystems (`gpio_pin_register()`)

## Verification
- Run: `./tools/configure.sh esp8684-devkitm:nsh && make`
