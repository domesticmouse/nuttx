# `esp32s3-ws-lcd128/src` Component (`boards/xtensa/esp32s3/esp32s3-ws-lcd128/src`)

## Overview
Board-level C implementation (`src`) for `esp32s3-ws-lcd128` (`xtensa/esp32s3`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 8 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[esp32s3-ws-lcd128.h:esp32s3_bringup]` Public declaration `esp32s3_bringup()`
- `[esp32s3-ws-lcd128.h:esp32s3_gpio_init]` Public declaration `esp32s3_gpio_init()`
- `[esp32s3-ws-lcd128.h:board_spiflash_init]` Public declaration `board_spiflash_init()`
- `[esp32s3-ws-lcd128.h:board_i2c_init]` Public declaration `board_i2c_init()`
- `[esp32s3-ws-lcd128.h:board_i2sdev_initialize]` Public declaration `board_i2sdev_initialize()`
- `[esp32s3-ws-lcd128.h:esp32s3_twai_setup]` Public declaration `esp32s3_twai_setup()`
- `[esp32s3-ws-lcd128.h:board_lcd_initialize]` Public declaration `board_lcd_initialize()`
- `[esp32s3-ws-lcd128.h:esp32s3_qmi8658_initialize]` Public declaration `esp32s3_qmi8658_initialize()`
- `[esp32s3-ws-lcd128.h:RMT_RXCHANNEL]` Hardware/board configuration macros (`RMT_RXCHANNEL`, `RMT_TXCHANNEL`, `RMT_INPUT_PIN`, `RMT_OUTPUT_PIN`, `DISPLAY_SPI`, `DISPLAY_RST` (+2 more))
- `[esp32s3_board_lcd_gc9a01.c:board_lcd_initialize]` Public function `board_lcd_initialize()`
- `[esp32s3_board_lcd_gc9a01.c:board_lcd_getdev]` Public function `board_lcd_getdev()`
- `[esp32s3_board_lcd_gc9a01.c:board_lcd_uninitialize]` Public function `board_lcd_uninitialize()`
- `[esp32s3_board_spi.c:esp32s3_spi2_select]` Public function `esp32s3_spi2_select()`
- `[esp32s3_board_spi.c:esp32s3_spi2_status]` Public function `esp32s3_spi2_status()`
- `[esp32s3_board_spi.c:esp32s3_spi2_cmddata]` Public function `esp32s3_spi2_cmddata()`
- `[esp32s3_board_spi.c:esp32s3_spi3_status]` Public function `esp32s3_spi3_status()`
- `[esp32s3_board_spi.c:esp32s3_spi3_cmddata]` Public function `esp32s3_spi3_cmddata()`
- `[esp32s3_boot.c:esp32s3_board_initialize]` Public function `esp32s3_board_initialize()`
- `[esp32s3_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[esp32s3_bringup.c:esp32s3_bringup]` Public function `esp32s3_bringup()`
- `[esp32s3_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[esp32s3_buttons.c:board_buttons]` Public function `board_buttons()`
- `[esp32s3_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[esp32s3_gpio.c:esp32s3_gpio_init]` Public function `esp32s3_gpio_init()`
- *(+1 additional symbols across 8 files)*

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_BUTTONS`, `CONFIG_BOARDCTL`, `CONFIG_BOARDCTL_RESET`, `CONFIG_DEV_GPIO`, `CONFIG_LCD_GC9A01` (+1 more)
- `[esp32s3-ws-lcd128.h:#error]` Compile-time guard: `CONFIG_ARCH_BOARD_ESP32S3_WS_LCD128_TOUCH is defined.`
- `[esp32s3-ws-lcd128.h:#error]` Compile-time guard: `CONFIG_ARCH_BOARD_ESP32S3_WS_LCD128_NOTOUCH is defined.`
- `[esp32s3_board_lcd_gc9a01.c:board_lcd_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[esp32s3_board_spi.c:esp32s3_spi2_select]` Validates preconditions and returns `-ENODEV` on failure
- `[esp32s3_buttons.c:DEBUGASSERT]` Requires `id == 0`
- `[esp32s3_gpio.c:DEBUGASSERT]` Requires `espgpio != NULL && value != NULL`
- `[esp32s3_gpio.c:DEBUGASSERT]` Requires `espgpio != NULL`
- `[esp32s3_gpio.c:DEBUGASSERT]` Requires `esp32s3gpio != NULL && value != NULL`
- `[esp32s3_gpio.c:#error]` Compile-time guard: `NGPIOINT is > 0 and GPIO interrupts aren't enabled`
- `[esp32s3_reset.c:#error]` Compile-time guard: `CONFIG_BOARD_ASSERT_RESET_VALUE must not be equal to EXIT_SUCCESS`

## Side Effects
- `[esp32s3_board_lcd_gc9a01.c:board_lcd_initialize]` Configures or drives hardware GPIO pins
- `[esp32s3_board_lcd_gc9a01.c:board_lcd_initialize]` Initializes/registers kernel devices or filesystems (`esp32s3_spibus_initialize()`)
- `[esp32s3_board_spi.c:esp32s3_spi2_select]` Configures or drives hardware GPIO pins
- `[esp32s3_bringup.c:esp32s3_bringup]` Initializes/registers kernel devices or filesystems (`board_bmp180_initialize()`, `board_capture_initialize()`, `board_i2sdev_initialize()`, `board_lcd_initialize()`, `board_motor_initialize()`)
- `[esp32s3_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[esp32s3_buttons.c:board_button_initialize]` Modifies interrupt controller or critical-section state
- `[esp32s3_gpio.c:esp32s3_gpio_init]` Configures or drives hardware GPIO pins
- `[esp32s3_gpio.c:esp32s3_gpio_init]` Initializes/registers kernel devices or filesystems (`gpio_pin_register()`)
- `[esp32s3_gpio.c:esp32s3_gpio_init]` Modifies interrupt controller or critical-section state

## Verification
- Run: `./tools/configure.sh esp32s3-ws-lcd128:nsh && make`
