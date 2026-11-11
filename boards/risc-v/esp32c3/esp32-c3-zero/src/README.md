# `esp32-c3-zero/src` Component (`boards/risc-v/esp32c3/esp32-c3-zero/src`)

## Overview
Board-level C implementation (`src`) for `esp32-c3-zero` (`risc-v/esp32c3`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 6 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[esp32-c3-zero.h:esp_bringup]` Public declaration `esp_bringup()`
- `[esp32-c3-zero.h:board_twai_setup]` Public declaration `board_twai_setup()`
- `[esp32-c3-zero.h:esp_gpio_init]` Public declaration `esp_gpio_init()`
- `[esp32-c3-zero.h:RMT_RXCHANNEL]` Hardware/board configuration macros (`RMT_RXCHANNEL`, `RMT_TXCHANNEL`, `RMT_INPUT_PIN`, `RMT_OUTPUT_PIN`)
- `[esp32c3_boot.c:esp_board_initialize]` Public function `esp_board_initialize()`
- `[esp32c3_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[esp32c3_bringup.c:esp_bringup]` Public function `esp_bringup()`
- `[esp32c3_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[esp32c3_buttons.c:board_buttons]` Public function `board_buttons()`
- `[esp32c3_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[esp32c3_gpio.c:esp_gpio_init]` Public function `esp_gpio_init()`
- `[esp32c3_reset.c:board_reset]` Public function `board_reset()`

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_BUTTONS`, `CONFIG_BOARDCTL_RESET`, `CONFIG_DEV_GPIO`
- `[esp32c3_buttons.c:DEBUGASSERT]` Requires `id == 0`
- `[esp32c3_gpio.c:DEBUGASSERT]` Requires `espgpio != NULL && value != NULL`
- `[esp32c3_gpio.c:DEBUGASSERT]` Requires `espgpio->id < BOARD_NGPIOOUT`
- `[esp32c3_gpio.c:DEBUGASSERT]` Requires `espgpio != NULL`
- `[esp32c3_gpio.c:#error]` Compile-time guard: `NGPIOINT is > 0 and GPIO interrupts aren't enabled`

## Side Effects
- `[esp32c3_bringup.c:esp_bringup]` Initializes/registers kernel devices or filesystems (`board_bmp180_initialize()`, `board_bmp280_initialize()`, `board_spidev_initialize()`, `board_spislavedev_initialize()`, `btn_lower_initialize()`)
- `[esp32c3_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[esp32c3_buttons.c:board_button_initialize]` Modifies interrupt controller or critical-section state
- `[esp32c3_gpio.c:esp_gpio_init]` Configures or drives hardware GPIO pins
- `[esp32c3_gpio.c:esp_gpio_init]` Initializes/registers kernel devices or filesystems (`gpio_pin_register()`)
- `[esp32c3_gpio.c:esp_gpio_init]` Modifies interrupt controller or critical-section state

## Verification
- Run: `./tools/configure.sh esp32-c3-zero:nsh && make`
