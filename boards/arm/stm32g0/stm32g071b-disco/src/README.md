# `stm32g071b-disco/src` Component (`boards/arm/stm32g0/stm32g071b-disco/src`)

## Overview
Board-level C implementation (`src`) for `stm32g071b-disco` (`arm/stm32g0`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 9 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[stm32g071b-disco.h:stm32_bringup]` Public declaration `stm32_bringup()`
- `[stm32g071b-disco.h:stm32_spidev_initialize]` Public declaration `stm32_spidev_initialize()`
- `[stm32g071b-disco.h:stm32_djoy_initialization]` Public declaration `stm32_djoy_initialization()`
- `[stm32g071b-disco.h:stm32_ina226_initialization]` Public declaration `stm32_ina226_initialization()`
- `[stm32g071b-disco.h:stm32_gpio_initialize]` Public declaration `stm32_gpio_initialize()`
- `[stm32g071b-disco.h:GPIO_LEDSINK]` Hardware/board configuration macros (`GPIO_LEDSINK`, `GPIO_LEDSOURCE`, `GPIO_LEDSPY`, `GPIO_LEDCC`, `LED_DRIVER_PATH`, `GPIO_JOY_SEL` (+17 more))
- `[stm32_boot.c:stm32_boardinitialize]` Public function `stm32_boardinitialize()`
- `[stm32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[stm32_bringup.c:stm32_bringup]` Public function `stm32_bringup()`
- `[stm32_djoystick.c:stm32_djoy_initialization]` Public function `stm32_djoy_initialization()`
- `[stm32_gpio.c:stm32_gpio_initialize]` Public function `stm32_gpio_initialize()`
- `[stm32_ina226.c:stm32_ina226_initialization]` Public function `stm32_ina226_initialization()`
- `[stm32_lcd_ssd1306.c:board_lcd_initialize]` Public function `board_lcd_initialize()`
- `[stm32_lcd_ssd1306.c:board_lcd_getdev]` Public function `board_lcd_getdev()`
- `[stm32_lcd_ssd1306.c:board_lcd_uninitialize]` Public function `board_lcd_uninitialize()`
- `[stm32_spi.c:stm32_spidev_initialize]` Public function `stm32_spidev_initialize()`
- `[stm32_spi.c:stm32_spi1select]` Public function `stm32_spi1select()`
- `[stm32_spi.c:stm32_spi1status]` Public function `stm32_spi1status()`
- `[stm32_spi.c:stm32_spi2select]` Public function `stm32_spi2select()`
- `[stm32_spi.c:stm32_spi2status]` Public function `stm32_spi2status()`
- `[stm32_spi.c:stm32_spi3select]` Public function `stm32_spi3select()`
- `[stm32_spi.c:stm32_spi3status]` Public function `stm32_spi3status()`
- `[stm32_spi.c:stm32_spi1cmddata]` Public function `stm32_spi1cmddata()`
- *(+5 additional symbols across 9 files)*

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_DEV_GPIO`, `CONFIG_INPUT_DJOYSTICK`, `CONFIG_LCD_SSD1306`, `CONFIG_SENSORS_INA226`, `CONFIG_SPI` (+1 more)
- `[stm32_djoystick.c:DEBUGASSERT]` Requires `g_djoyhandler`
- `[stm32_gpio.c:DEBUGASSERT]` Requires `stm32gpint != NULL && stm32gpint->callback != NULL`
- `[stm32_gpio.c:DEBUGASSERT]` Requires `stm32gpio != NULL && value != NULL`
- `[stm32_gpio.c:DEBUGASSERT]` Requires `stm32gpio->id < BOARD_NGPIOIN`
- `[stm32_ina226.c:#error]` Compile-time guard: `I2C1 must be enabled!`

## Side Effects
- `[stm32_boot.c:stm32_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `stm32_spidev_initialize()`)
- `[stm32_bringup.c:stm32_bringup]` Initializes/registers kernel devices or filesystems (`board_lcd_initialize()`, `stm32_gpio_initialize()`, `userled_lower_initialize()`)
- `[stm32_djoystick.c:stm32_djoy_initialization]` Configures or drives hardware GPIO pins
- `[stm32_djoystick.c:stm32_djoy_initialization]` Initializes/registers kernel devices or filesystems (`djoy_register()`)
- `[stm32_djoystick.c:stm32_djoy_initialization]` Modifies interrupt controller or critical-section state
- `[stm32_gpio.c:stm32_gpio_initialize]` Configures or drives hardware GPIO pins
- `[stm32_gpio.c:stm32_gpio_initialize]` Initializes/registers kernel devices or filesystems (`gpio_pin_register()`)
- `[stm32_ina226.c:stm32_ina226_initialization]` Initializes/registers kernel devices or filesystems (`ina226_register()`, `stm32_i2cbus_initialize()`)
- `[stm32_lcd_ssd1306.c:board_lcd_initialize]` Configures or drives hardware GPIO pins
- `[stm32_lcd_ssd1306.c:board_lcd_initialize]` Initializes/registers kernel devices or filesystems (`board_ssd1306_initialize()`)
- `[stm32_spi.c:stm32_spidev_initialize]` Configures or drives hardware GPIO pins
- `[stm32_spi.c:stm32_spidev_initialize]` Initializes/registers kernel devices or filesystems (`stm32_spibus_initialize()`)

## Verification
- Run: `./tools/configure.sh stm32g071b-disco:nsh && make`
