# `common/src` Component (`boards/risc-v/esp32c3-legacy/common/src`)

## Overview
Board-level C implementation (`src`) for `common` (`risc-v/esp32c3-legacy`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 19 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[esp32c3_board_adc.c:board_adc_init]` Public function `board_adc_init()`
- `[esp32c3_board_apa102.c:board_lcd_initialize]` Public function `board_lcd_initialize()`
- `[esp32c3_board_apa102.c:board_lcd_getdev]` Public function `board_lcd_getdev()`
- `[esp32c3_board_apa102.c:board_lcd_uninitialize]` Public function `board_lcd_uninitialize()`
- `[esp32c3_board_apds9960.c:board_apds9960_initialize]` Public function `board_apds9960_initialize()`
- `[esp32c3_board_bmp180.c:board_bmp180_initialize]` Public function `board_bmp180_initialize()`
- `[esp32c3_board_gc9a01.c:board_lcd_initialize]` Public function `board_lcd_initialize()`
- `[esp32c3_board_gc9a01.c:board_lcd_getdev]` Public function `board_lcd_getdev()`
- `[esp32c3_board_gc9a01.c:board_lcd_uninitialize]` Public function `board_lcd_uninitialize()`
- `[esp32c3_board_i2c.c:board_i2c_init]` Public function `board_i2c_init()`
- `[esp32c3_board_ice40.c:esp32c3_ice40_setup]` Public function `esp32c3_ice40_setup()`
- `[esp32c3_board_ledc.c:board_ledc_setup]` Public function `board_ledc_setup()`
- `[esp32c3_board_mpu60x0_i2c.c:board_mpu60x0_initialize]` Public function `board_mpu60x0_initialize()`
- `[esp32c3_board_oneshot.c:board_oneshot_init]` Public function `board_oneshot_init()`
- `[esp32c3_board_spi.c:esp32c3_spi2_status]` Public function `esp32c3_spi2_status()`
- `[esp32c3_board_spi.c:esp32c3_spi2_cmddata]` Public function `esp32c3_spi2_cmddata()`
- `[esp32c3_board_spidev.c:board_spidev_initialize]` Public function `board_spidev_initialize()`
- `[esp32c3_board_spiflash.c:board_spiflash_init]` Public function `board_spiflash_init()`
- `[esp32c3_board_spislavedev.c:board_spislavedev_initialize]` Public function `board_spislavedev_initialize()`
- `[esp32c3_board_st7735.c:board_lcd_initialize]` Public function `board_lcd_initialize()`
- `[esp32c3_board_st7735.c:board_lcd_getdev]` Public function `board_lcd_getdev()`
- `[esp32c3_board_st7735.c:board_lcd_uninitialize]` Public function `board_lcd_uninitialize()`
- `[esp32c3_board_st7789.c:board_lcd_initialize]` Public function `board_lcd_initialize()`
- *(+5 additional symbols across 19 files)*

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ADC`, `CONFIG_ARCH`, `CONFIG_ARCH_BOARD_COMMON`, `CONFIG_CAN`, `CONFIG_ESP32C3_SPI`, `CONFIG_ESP32C3_SPIFLASH` (+15 more)
- `[esp32c3_board_adc.c:board_adc_init]` Validates preconditions and returns `-ENODEV` on failure
- `[esp32c3_board_apa102.c:board_lcd_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[esp32c3_board_apds9960.c:board_apds9960_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[esp32c3_board_bmp180.c:board_bmp180_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[esp32c3_board_gc9a01.c:#error]` Compile-time guard: `The GC9A01 driver requires CONFIG_SPI_CMDATA in the config`
- `[esp32c3_board_gc9a01.c:#error]` Compile-time guard: `The GC9A01 driver requires CONFIG_ESP32C3_SPI_SWCS in the config`
- `[esp32c3_board_i2c.c:board_i2c_init]` Validates preconditions and returns `-ENODEV` on failure
- `[esp32c3_board_ice40.c:esp32c3_ice40_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[esp32c3_board_ledc.c:board_ledc_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[esp32c3_board_mpu60x0_i2c.c:board_mpu60x0_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[esp32c3_board_oneshot.c:board_oneshot_init]` Validates preconditions and returns `-EBUSY` on failure

## Side Effects
- `[esp32c3_board_adc.c:board_adc_init]` Initializes/registers kernel devices or filesystems (`adc_register()`)
- `[esp32c3_board_apa102.c:board_lcd_initialize]` Initializes/registers kernel devices or filesystems (`apa102_initialize()`, `esp32c3_spibus_initialize()`)
- `[esp32c3_board_apds9960.c:board_apds9960_initialize]` Configures or drives hardware GPIO pins
- `[esp32c3_board_apds9960.c:board_apds9960_initialize]` Initializes/registers kernel devices or filesystems (`apds9960_register()`, `esp32c3_i2cbus_initialize()`)
- `[esp32c3_board_apds9960.c:board_apds9960_initialize]` Modifies interrupt controller or critical-section state
- `[esp32c3_board_bmp180.c:board_bmp180_initialize]` Initializes/registers kernel devices or filesystems (`bmp180_register()`, `esp32c3_i2cbus_initialize()`)
- `[esp32c3_board_gc9a01.c:board_lcd_initialize]` Configures or drives hardware GPIO pins
- `[esp32c3_board_gc9a01.c:board_lcd_initialize]` Initializes/registers kernel devices or filesystems (`esp32c3_spibus_initialize()`)
- `[esp32c3_board_i2c.c:board_i2c_init]` Initializes/registers kernel devices or filesystems (`esp32c3_i2cbus_initialize()`, `i2c_register()`)
- `[esp32c3_board_ice40.c:esp32c3_ice40_setup]` Initializes/registers kernel devices or filesystems (`esp32c3_ice40_initialize()`, `ice40_register()`)
- `[esp32c3_board_ledc.c:board_ledc_setup]` Initializes/registers kernel devices or filesystems (`pwm_register()`)
- `[esp32c3_board_mpu60x0_i2c.c:board_mpu60x0_initialize]` Initializes/registers kernel devices or filesystems (`esp32c3_i2cbus_initialize()`, `mpu60x0_register()`)

## Verification
- Run: `./tools/configure.sh sim:nsh && make`
