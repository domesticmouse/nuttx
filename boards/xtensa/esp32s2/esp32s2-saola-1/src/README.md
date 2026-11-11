# `esp32s2-saola-1/src` Component (`boards/xtensa/esp32s2/esp32s2-saola-1/src`)

## Overview
Board-level C implementation (`src`) for `esp32s2-saola-1` (`xtensa/esp32s2`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 10 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[esp32s2-saola-1.h:esp32s2_bringup]` Public declaration `esp32s2_bringup()`
- `[esp32s2-saola-1.h:board_spiflash_init]` Public declaration `board_spiflash_init()`
- `[esp32s2-saola-1.h:esp32s2_gpio_init]` Public declaration `esp32s2_gpio_init()`
- `[esp32s2-saola-1.h:board_oneshot_init]` Public declaration `board_oneshot_init()`
- `[esp32s2-saola-1.h:board_i2c_init]` Public declaration `board_i2c_init()`
- `[esp32s2-saola-1.h:board_bmp180_initialize]` Public declaration `board_bmp180_initialize()`
- `[esp32s2-saola-1.h:board_i2sdev_initialize]` Public declaration `board_i2sdev_initialize()`
- `[esp32s2-saola-1.h:esp32s2_cs4344_initialize]` Public declaration `esp32s2_cs4344_initialize()`
- `[esp32s2-saola-1.h:esp32s2_pwm_setup]` Public declaration `esp32s2_pwm_setup()`
- `[esp32s2-saola-1.h:board_twai_setup]` Public declaration `board_twai_setup()`
- `[esp32s2-saola-1.h:BUTTON_BOOT]` Hardware/board configuration macros (`BUTTON_BOOT`, `TIMER0`, `TIMER1`, `TIMER2`, `TIMER3`, `ONESHOT_TIMER` (+5 more))
- `[esp32s2_bmp180.c:board_bmp180_initialize]` Public function `board_bmp180_initialize()`
- `[esp32s2_board_i2c.c:board_i2c_init]` Public function `board_i2c_init()`
- `[esp32s2_boot.c:esp32s2_board_initialize]` Public function `esp32s2_board_initialize()`
- `[esp32s2_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[esp32s2_bringup.c:esp32s2_bringup]` Public function `esp32s2_bringup()`
- `[esp32s2_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[esp32s2_buttons.c:board_buttons]` Public function `board_buttons()`
- `[esp32s2_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[esp32s2_gpio.c:esp32s2_gpio_init]` Public function `esp32s2_gpio_init()`
- `[esp32s2_ledc.c:esp32s2_pwm_setup]` Public function `esp32s2_pwm_setup()`
- `[esp32s2_oneshot.c:board_oneshot_init]` Public function `board_oneshot_init()`
- `[esp32s2_reset.c:board_reset]` Public function `board_reset()`

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_BUTTONS`, `CONFIG_BOARDCTL_RESET`, `CONFIG_DEV_GPIO`, `CONFIG_I2C_DRIVER`, `CONFIG_ONESHOT` (+2 more)
- `[esp32s2_bmp180.c:board_bmp180_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[esp32s2_board_i2c.c:board_i2c_init]` Validates preconditions and returns `-ENODEV` on failure
- `[esp32s2_gpio.c:DEBUGASSERT]` Requires `espgpio != NULL && value != NULL`
- `[esp32s2_gpio.c:DEBUGASSERT]` Requires `espgpio != NULL`
- `[esp32s2_gpio.c:DEBUGASSERT]` Requires `esp32s2gpio != NULL && value != NULL`
- `[esp32s2_gpio.c:#error]` Compile-time guard: `NGPIOINT is > 0 and GPIO interrupts aren't enabled`
- `[esp32s2_ledc.c:esp32s2_pwm_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[esp32s2_oneshot.c:board_oneshot_init]` Validates preconditions and returns `-EBUSY` on failure

## Side Effects
- `[esp32s2_bmp180.c:board_bmp180_initialize]` Initializes/registers kernel devices or filesystems (`bmp180_register()`, `esp32s2_i2cbus_initialize()`)
- `[esp32s2_board_i2c.c:board_i2c_init]` Initializes/registers kernel devices or filesystems (`esp32s2_i2cbus_initialize()`, `i2c_register()`)
- `[esp32s2_bringup.c:esp32s2_bringup]` Initializes/registers kernel devices or filesystems (`board_bmp180_initialize()`, `board_i2sdev_initialize()`, `board_max6675_initialize()`, `board_pcnt_initialize()`, `board_sdmmc_initialize()`)
- `[esp32s2_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[esp32s2_gpio.c:esp32s2_gpio_init]` Configures or drives hardware GPIO pins
- `[esp32s2_gpio.c:esp32s2_gpio_init]` Initializes/registers kernel devices or filesystems (`gpio_pin_register()`)
- `[esp32s2_ledc.c:esp32s2_pwm_setup]` Initializes/registers kernel devices or filesystems (`pwm_register()`)
- `[esp32s2_oneshot.c:board_oneshot_init]` Initializes/registers kernel devices or filesystems (`oneshot_initialize()`, `oneshot_register()`)

## Verification
- Run: `./tools/configure.sh esp32s2-saola-1:nsh && make`
