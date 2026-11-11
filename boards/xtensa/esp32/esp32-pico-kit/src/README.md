# `esp32-pico-kit/src` Component (`boards/xtensa/esp32/esp32-pico-kit/src`)

## Overview
Board-level C implementation (`src`) for `esp32-pico-kit` (`xtensa/esp32`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 8 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[esp32-pico-kit.h:esp32_bringup]` Public declaration `esp32_bringup()`
- `[esp32-pico-kit.h:esp32_gpio_init]` Public declaration `esp32_gpio_init()`
- `[esp32-pico-kit.h:esp32_pwm_setup]` Public declaration `esp32_pwm_setup()`
- `[esp32-pico-kit.h:board_spidev_initialize]` Public declaration `board_spidev_initialize()`
- `[esp32-pico-kit.h:esp32_twai_setup]` Public declaration `esp32_twai_setup()`
- `[esp32-pico-kit.h:board_i2sdev_initialize]` Public declaration `board_i2sdev_initialize()`
- `[esp32-pico-kit.h:BUTTON_BOOT]` Hardware/board configuration macros (`BUTTON_BOOT`, `GPIO_LED1`, `PCNT_QE0_ID`, `GPIO_MCP2515_IRQ`, `TIMER0`, `TIMER1` (+4 more))
- `[esp32_boot.c:esp32_board_initialize]` Public function `esp32_board_initialize()`
- `[esp32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[esp32_bringup.c:esp32_bringup]` Public function `esp32_bringup()`
- `[esp32_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[esp32_buttons.c:board_buttons]` Public function `board_buttons()`
- `[esp32_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[esp32_gpio.c:esp32_gpio_init]` Public function `esp32_gpio_init()`
- `[esp32_ledc.c:esp32_pwm_setup]` Public function `esp32_pwm_setup()`
- `[esp32_reset.c:board_reset]` Public function `board_reset()`
- `[esp32_twai.c:esp32_twai_setup]` Public function `esp32_twai_setup()`

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_BUTTONS`, `CONFIG_BOARDCTL_RESET`, `CONFIG_DEV_GPIO`, `CONFIG_ESP32_TWAI`, `CONFIG_PWM`
- `[esp32_gpio.c:DEBUGASSERT]` Requires `esp32gpio != NULL && value != NULL`
- `[esp32_gpio.c:DEBUGASSERT]` Requires `esp32gpio->id < BOARD_NGPIOOUT`
- `[esp32_gpio.c:DEBUGASSERT]` Requires `esp32gpio != NULL`
- `[esp32_gpio.c:#error]` Compile-time guard: `NGPIOINT is > 0 and GPIO interrupts aren't enabled`
- `[esp32_ledc.c:esp32_pwm_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[esp32_reset.c:#error]` Compile-time guard: `CONFIG_BOARD_ASSERT_RESET_VALUE must not be equal to EXIT_SUCCESS`
- `[esp32_twai.c:esp32_twai_setup]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[esp32_bringup.c:esp32_bringup]` Initializes/registers kernel devices or filesystems (`board_i2sdev_initialize()`, `board_spidev_initialize()`, `btn_lower_initialize()`, `esp32_ble_initialize()`, `esp32_i2c_register()`)
- `[esp32_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[esp32_gpio.c:esp32_gpio_init]` Configures or drives hardware GPIO pins
- `[esp32_gpio.c:esp32_gpio_init]` Initializes/registers kernel devices or filesystems (`gpio_pin_register()`)
- `[esp32_ledc.c:esp32_pwm_setup]` Initializes/registers kernel devices or filesystems (`pwm_register()`)
- `[esp32_twai.c:esp32_twai_setup]` Initializes/registers kernel devices or filesystems (`can_register()`)

## Verification
- Run: `./tools/configure.sh esp32-pico-kit:nsh && make`
