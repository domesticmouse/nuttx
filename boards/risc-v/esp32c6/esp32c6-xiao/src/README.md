# `esp32c6-xiao/src` Component (`boards/risc-v/esp32c6/esp32c6-xiao/src`)

## Overview
Board-level C implementation (`src`) for `esp32c6-xiao` (`risc-v/esp32c6`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 5 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[esp32c6-xiao.h:esp_bringup]` Public declaration `esp_bringup()`
- `[esp32c6-xiao.h:board_twai_setup]` Public declaration `board_twai_setup()`
- `[esp32c6-xiao.h:esp_gpio_init]` Public declaration `esp_gpio_init()`
- `[esp32c6-xiao.h:RMT_RXCHANNEL]` Hardware/board configuration macros (`RMT_RXCHANNEL`, `RMT_TXCHANNEL`, `RMT_INPUT_PIN`, `RMT_OUTPUT_PIN`)
- `[esp32c6_boot.c:esp_board_initialize]` Public function `esp_board_initialize()`
- `[esp32c6_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[esp32c6_bringup.c:esp_bringup]` Public function `esp_bringup()`
- `[esp32c6_gpio.c:esp_gpio_init]` Public function `esp_gpio_init()`
- `[esp32c6_reset.c:board_reset]` Public function `board_reset()`

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_BOARDCTL_RESET`, `CONFIG_DEV_GPIO`
- `[esp32c6_gpio.c:DEBUGASSERT]` Requires `espgpio != NULL && value != NULL`
- `[esp32c6_gpio.c:DEBUGASSERT]` Requires `espgpio->id < BOARD_NGPIOOUT`
- `[esp32c6_gpio.c:DEBUGASSERT]` Requires `espgpio != NULL`
- `[esp32c6_gpio.c:#error]` Compile-time guard: `NGPIOINT is > 0 and GPIO interrupts aren't enabled`

## Side Effects
- `[esp32c6_bringup.c:esp_bringup]` Initializes/registers kernel devices or filesystems (`board_spidev_initialize()`, `board_spislavedev_initialize()`, `esp_coex_adapter_register()`, `esp_efuse_initialize()`, `esp_nxdiag_initialize()`)
- `[esp32c6_gpio.c:esp_gpio_init]` Configures or drives hardware GPIO pins
- `[esp32c6_gpio.c:esp_gpio_init]` Initializes/registers kernel devices or filesystems (`gpio_pin_register()`)

## Verification
- Run: `./tools/configure.sh esp32c6-xiao:nsh && make`
