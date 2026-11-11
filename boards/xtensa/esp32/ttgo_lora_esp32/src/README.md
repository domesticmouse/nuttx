# `ttgo_lora_esp32/src` Component (`boards/xtensa/esp32/ttgo_lora_esp32/src`)

## Overview
Board-level C implementation (`src`) for `ttgo_lora_esp32` (`xtensa/esp32`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 8 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[ttgo_lora_esp32.h:esp32_bringup]` Public declaration `esp32_bringup()`
- `[ttgo_lora_esp32.h:esp32_mmcsd_initialize]` Public declaration `esp32_mmcsd_initialize()`
- `[ttgo_lora_esp32.h:esp32_spiflash_init]` Public declaration `esp32_spiflash_init()`
- `[ttgo_lora_esp32.h:esp32_gpio_init]` Public declaration `esp32_gpio_init()`
- `[ttgo_lora_esp32.h:board_spidev_initialize]` Public declaration `board_spidev_initialize()`
- `[ttgo_lora_esp32.h:esp32_lpwaninitialize]` Public declaration `esp32_lpwaninitialize()`
- `[ttgo_lora_esp32.h:GPIO_SX127X_RESET]` Hardware/board configuration macros (`GPIO_SX127X_RESET`, `GPIO_SX127X_DIO0`, `BUTTON_BOOT`, `GPIO_LED1`, `GPIO_MCP2515_IRQ`, `TIMER0` (+5 more))
- `[esp32_boot.c:esp32_board_initialize]` Public function `esp32_board_initialize()`
- `[esp32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[esp32_bringup.c:esp32_bringup]` Public function `esp32_bringup()`
- `[esp32_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[esp32_buttons.c:board_buttons]` Public function `board_buttons()`
- `[esp32_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[esp32_gpio.c:esp32_gpio_init]` Public function `esp32_gpio_init()`
- `[esp32_reset.c:board_reset]` Public function `board_reset()`
- `[esp32_sx127x.c:esp32_lpwaninitialize]` Public function `esp32_lpwaninitialize()`
- `[esp32_userleds.c:board_userled_initialize]` Public function `board_userled_initialize()`
- `[esp32_userleds.c:board_userled]` Public function `board_userled()`
- `[esp32_userleds.c:board_userled_all]` Public function `board_userled_all()`

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_BUTTONS`, `CONFIG_BOARDCTL_RESET`, `CONFIG_DEV_GPIO`, `CONFIG_LPWAN_SX127X`, `CONFIG_MMCSD` (+1 more)
- `[esp32_gpio.c:DEBUGASSERT]` Requires `esp32gpio != NULL && value != NULL`
- `[esp32_gpio.c:DEBUGASSERT]` Requires `esp32gpio->id < BOARD_NGPIOOUT`
- `[esp32_gpio.c:DEBUGASSERT]` Requires `esp32gpio != NULL`
- `[esp32_gpio.c:#error]` Compile-time guard: `NGPIOINT is > 0 and GPIO interrupts aren't enabled`
- `[esp32_sx127x.c:esp32_lpwaninitialize]` Validates preconditions and returns `-EINVAL`, `-ENODEV` on failure

## Side Effects
- `[esp32_bringup.c:esp32_bringup]` Initializes/registers kernel devices or filesystems (`board_bmp180_initialize()`, `board_ht16k33_initialize()`, `board_mcp2515_initialize()`, `board_spidev_initialize()`, `btn_lower_initialize()`)
- `[esp32_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[esp32_gpio.c:esp32_gpio_init]` Configures or drives hardware GPIO pins
- `[esp32_gpio.c:esp32_gpio_init]` Initializes/registers kernel devices or filesystems (`gpio_pin_register()`)
- `[esp32_sx127x.c:esp32_lpwaninitialize]` Configures or drives hardware GPIO pins
- `[esp32_sx127x.c:esp32_lpwaninitialize]` Initializes/registers kernel devices or filesystems (`esp32_spibus_initialize()`, `sx127x_register()`)
- `[esp32_userleds.c:board_userled_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh ttgo_lora_esp32:nsh && make`
