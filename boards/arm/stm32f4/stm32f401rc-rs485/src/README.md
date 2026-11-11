# `stm32f401rc-rs485/src` Component (`boards/arm/stm32f4/stm32f401rc-rs485/src`)

## Overview
Board-level C implementation (`src`) for `stm32f401rc-rs485` (`arm/stm32f4`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 17 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[stm32f401rc-rs485.h:stm32_bringup]` Public declaration `stm32_bringup()`
- `[stm32f401rc-rs485.h:stm32_spidev_initialize]` Public declaration `stm32_spidev_initialize()`
- `[stm32f401rc-rs485.h:stm32_usbinitialize]` Public declaration `stm32_usbinitialize()`
- `[stm32f401rc-rs485.h:stm32_adc_setup]` Public declaration `stm32_adc_setup()`
- `[stm32f401rc-rs485.h:stm32_pwm_setup]` Public declaration `stm32_pwm_setup()`
- `[stm32f401rc-rs485.h:stm32_sdio_initialize]` Public declaration `stm32_sdio_initialize()`
- `[stm32f401rc-rs485.h:stm32_i2cbus_initialize]` Public declaration `stm32_i2cbus_initialize()`
- `[stm32f401rc-rs485.h:stm32_at24_init]` Public declaration `stm32_at24_init()`
- `[stm32f401rc-rs485.h:stm32_gpio_initialize]` Public declaration `stm32_gpio_initialize()`
- `[stm32f401rc-rs485.h:stm32_hx711_initialize]` Public declaration `stm32_hx711_initialize()`
- `[stm32f401rc-rs485.h:HAVE_SDIO]` Hardware/board configuration macros (`HAVE_SDIO`, `SDIO_MINOR`, `SDIO_SLOTNO`, `GPIO_SDIO_NCD`, `GPIO_LED1`, `GPIO_LED2` (+28 more))
- `[stm32_adc.c:stm32_adc_setup]` Public function `stm32_adc_setup()`
- `[stm32_at24.c:stm32_at24_init]` Public function `stm32_at24_init()`
- `[stm32_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[stm32_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[stm32_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[stm32_boot.c:stm32_boardinitialize]` Public function `stm32_boardinitialize()`
- `[stm32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[stm32_bringup.c:stm32_bringup]` Public function `stm32_bringup()`
- `[stm32_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[stm32_buttons.c:board_buttons]` Public function `board_buttons()`
- `[stm32_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[stm32_gpio.c:stm32_gpio_initialize]` Public function `stm32_gpio_initialize()`
- *(+27 additional symbols across 17 files)*

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ADC`, `CONFIG_ADC_HX711`, `CONFIG_ARCH`, `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_DEV_GPIO` (+9 more)
- `[stm32_adc.c:stm32_adc_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_at24.c:stm32_at24_init]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure
- `[stm32_gpio.c:DEBUGASSERT]` Requires `stm32gpint != NULL && stm32gpint->callback != NULL`
- `[stm32_gpio.c:DEBUGASSERT]` Requires `stm32gpio != NULL && value != NULL`
- `[stm32_gpio.c:DEBUGASSERT]` Requires `stm32gpio->id < BOARD_NGPIOIN`
- `[stm32_lcd_st7735.c:board_lcd_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_pwm.c:stm32_pwm_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_sdio.c:stm32_sdio_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_spi.c:stm32_spidev_initialize]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[stm32_adc.c:stm32_adc_setup]` Configures or drives hardware GPIO pins
- `[stm32_adc.c:stm32_adc_setup]` Initializes/registers kernel devices or filesystems (`adc_register()`)
- `[stm32_at24.c:stm32_at24_init]` Initializes/registers kernel devices or filesystems (`ee24xx_initialize()`, `stm32_i2cbus_initialize()`)
- `[stm32_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[stm32_boot.c:stm32_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `stm32_spidev_initialize()`)
- `[stm32_bringup.c:stm32_bringup]` Initializes/registers kernel devices or filesystems (`board_bmp180_initialize()`, `board_bmp280_initialize()`, `board_drv8825_initialize()`, `board_hcsr04_initialize()`, `board_lm75_initialize()`)
- `[stm32_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[stm32_gpio.c:stm32_gpio_initialize]` Configures or drives hardware GPIO pins
- `[stm32_gpio.c:stm32_gpio_initialize]` Initializes/registers kernel devices or filesystems (`gpio_pin_register()`)
- `[stm32_hx711.c:stm32_hx711_initialize]` Configures or drives hardware GPIO pins
- `[stm32_hx711.c:stm32_hx711_initialize]` Initializes/registers kernel devices or filesystems (`hx711_register()`)
- `[stm32_lcd_ssd1306.c:board_lcd_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh stm32f401rc-rs485:nsh && make`
