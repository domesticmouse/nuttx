# `esp32-m5-stickc-plus/src` Component (`boards/xtensa/esp32/esp32-m5-stickc-plus/src`)

## Overview
Board-level C implementation (`src`) for `esp32-m5-stickc-plus` (`xtensa/esp32`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 9 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[esp32-m5-stickc-plus.h:esp32_bringup]` Public declaration `esp32_bringup()`
- `[esp32-m5-stickc-plus.h:esp32_pwm_setup]` Public declaration `esp32_pwm_setup()`
- `[esp32-m5-stickc-plus.h:board_axp192_initialize]` Public declaration `board_axp192_initialize()`
- `[esp32-m5-stickc-plus.h:board_bm8563_initialize]` Public declaration `board_bm8563_initialize()`
- `[esp32-m5-stickc-plus.h:BUTTON_A]` Hardware/board configuration macros (`BUTTON_A`, `BUTTON_B`, `GPIO_LED1`, `GPIO_BUZZER`, `AXP192_I2C_PORT`, `BM8563_I2C_PORT` (+8 more))
- `[esp32_axp192.c:board_axp192_initialize]` Public function `board_axp192_initialize()`
- `[esp32_bm8563.c:up_rtc_initialize]` Public function `up_rtc_initialize()`
- `[esp32_bm8563.c:board_bm8563_initialize]` Public function `board_bm8563_initialize()`
- `[esp32_boot.c:esp32_board_initialize]` Public function `esp32_board_initialize()`
- `[esp32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[esp32_bringup.c:esp32_bringup]` Public function `esp32_bringup()`
- `[esp32_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[esp32_buttons.c:board_buttons]` Public function `board_buttons()`
- `[esp32_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[esp32_ledc.c:esp32_pwm_setup]` Public function `esp32_pwm_setup()`
- `[esp32_reset.c:board_reset]` Public function `board_reset()`
- `[esp32_userleds.c:board_userled_initialize]` Public function `board_userled_initialize()`
- `[esp32_userleds.c:board_userled]` Public function `board_userled()`
- `[esp32_userleds.c:board_userled_all]` Public function `board_userled_all()`

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_BUTTONS`, `CONFIG_BOARDCTL_RESET`, `CONFIG_ESP32_I2C0`, `CONFIG_PWM`, `CONFIG_RTC_PCF8563` (+1 more)
- `[esp32_axp192.c:board_axp192_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[esp32_bm8563.c:up_rtc_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[esp32_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure
- `[esp32_ledc.c:esp32_pwm_setup]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[esp32_axp192.c:board_axp192_initialize]` Initializes/registers kernel devices or filesystems (`esp32_i2cbus_initialize()`)
- `[esp32_bm8563.c:up_rtc_initialize]` Initializes/registers kernel devices or filesystems (`esp32_i2cbus_initialize()`, `pcf8563_rtc_initialize()`)
- `[esp32_bringup.c:esp32_bringup]` Initializes/registers kernel devices or filesystems (`board_axp192_initialize()`, `board_bm8563_initialize()`, `board_lcd_initialize()`, `btn_lower_initialize()`, `esp32_ble_initialize()`)
- `[esp32_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[esp32_ledc.c:esp32_pwm_setup]` Initializes/registers kernel devices or filesystems (`pwm_register()`)
- `[esp32_userleds.c:board_userled_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh esp32-m5-stickc-plus:nsh && make`
