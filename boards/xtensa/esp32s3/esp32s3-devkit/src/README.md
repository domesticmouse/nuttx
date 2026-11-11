# `esp32s3-devkit/src` Component (`boards/xtensa/esp32s3/esp32s3-devkit/src`)

## Overview
Board-level C implementation (`src`) for `esp32s3-devkit` (`xtensa/esp32s3`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 12 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[esp32s3-devkit.h:esp32s3_bringup]` Public declaration `esp32s3_bringup()`
- `[esp32s3-devkit.h:esp32s3_gpio_init]` Public declaration `esp32s3_gpio_init()`
- `[esp32s3-devkit.h:board_spiflash_init]` Public declaration `board_spiflash_init()`
- `[esp32s3-devkit.h:board_i2c_init]` Public declaration `board_i2c_init()`
- `[esp32s3-devkit.h:board_bmp180_initialize]` Public declaration `board_bmp180_initialize()`
- `[esp32s3-devkit.h:board_i2sdev_initialize]` Public declaration `board_i2sdev_initialize()`
- `[esp32s3-devkit.h:esp32s3_cs4344_initialize]` Public declaration `esp32s3_cs4344_initialize()`
- `[esp32s3-devkit.h:esp32s3_djoy_initialize]` Public declaration `esp32s3_djoy_initialize()`
- `[esp32s3-devkit.h:esp32s3_twai_setup]` Public declaration `esp32s3_twai_setup()`
- `[esp32s3-devkit.h:esp32s3_lan9250_initialize]` Public declaration `esp32s3_lan9250_initialize()`
- `[esp32s3-devkit.h:esp32s3_lan9250_uninitialize]` Public declaration `esp32s3_lan9250_uninitialize()`
- `[esp32s3-devkit.h:esp_openeth_initialize]` Public declaration `esp_openeth_initialize()`
- `[esp32s3-devkit.h:GPIO_LCD_DC]` Hardware/board configuration macros (`GPIO_LCD_DC`, `GPIO_LCD_RST`, `BUTTON_BOOT`, `RMT_RXCHANNEL`, `RMT_TXCHANNEL`, `RMT_INPUT_PIN` (+1 more))
- `[romfs.h]` Board header declarations `romfs.h`
- `[esp32s3_board_spi.c:esp32s3_spi2_status]` Public function `esp32s3_spi2_status()`
- `[esp32s3_board_spi.c:esp32s3_spi2_cmddata]` Public function `esp32s3_spi2_cmddata()`
- `[esp32s3_board_spi.c:esp32s3_spi3_status]` Public function `esp32s3_spi3_status()`
- `[esp32s3_board_spi.c:esp32s3_spi3_cmddata]` Public function `esp32s3_spi3_cmddata()`
- `[esp32s3_boot.c:esp32s3_board_initialize]` Public function `esp32s3_board_initialize()`
- `[esp32s3_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[esp32s3_bringup.c:esp32s3_bringup]` Public function `esp32s3_bringup()`
- `[esp32s3_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[esp32s3_buttons.c:board_buttons]` Public function `board_buttons()`
- *(+9 additional symbols across 12 files)*

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_BUTTONS`, `CONFIG_BOARDCTL_RESET`, `CONFIG_BUILD_KERNEL`, `CONFIG_DEV_GPIO`, `CONFIG_ESP32S3_SPI` (+4 more)
- `[esp32s3_board_spi.c:esp32s3_spi2_status]` Validates preconditions and returns `-ENODEV` on failure
- `[esp32s3_djoystick.c:DEBUGASSERT]` Requires `g_djoyhandler`
- `[esp32s3_gpio.c:DEBUGASSERT]` Requires `esp32s3gpio != NULL && value != NULL`
- `[esp32s3_gpio.c:DEBUGASSERT]` Requires `esp32s3gpio != NULL`
- `[esp32s3_gpio.c:#error]` Compile-time guard: `NGPIOINT is > 0 and GPIO interrupts aren't enabled`
- `[esp32s3_reset.c:#error]` Compile-time guard: `CONFIG_BOARD_ASSERT_RESET_VALUE must not be equal to EXIT_SUCCESS`
- `[esp32s3_st7735.c:board_lcd_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[esp32s3_twai.c:esp32s3_twai_setup]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[esp32s3_board_spi.c:esp32s3_spi2_status]` Configures or drives hardware GPIO pins
- `[esp32s3_bringup.c:esp32s3_bringup]` Initializes/registers kernel devices or filesystems (`board_bmp180_initialize()`, `board_capture_initialize()`, `board_i2sdev_initialize()`, `board_lcd_initialize()`, `board_motor_initialize()`)
- `[esp32s3_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[esp32s3_djoystick.c:esp32s3_djoy_initialize]` Configures or drives hardware GPIO pins
- `[esp32s3_djoystick.c:esp32s3_djoy_initialize]` Initializes/registers kernel devices or filesystems (`djoy_register()`)
- `[esp32s3_djoystick.c:esp32s3_djoy_initialize]` Modifies interrupt controller or critical-section state
- `[esp32s3_gpio.c:esp32s3_gpio_init]` Configures or drives hardware GPIO pins
- `[esp32s3_gpio.c:esp32s3_gpio_init]` Initializes/registers kernel devices or filesystems (`gpio_pin_register()`)
- `[esp32s3_st7735.c:board_lcd_initialize]` Configures or drives hardware GPIO pins
- `[esp32s3_st7735.c:board_lcd_initialize]` Initializes/registers kernel devices or filesystems (`esp32s3_spibus_initialize()`)
- `[esp32s3_twai.c:esp32s3_twai_setup]` Initializes/registers kernel devices or filesystems (`can_register()`)

## Verification
- Run: `./tools/configure.sh esp32s3-devkit:nsh && make`
