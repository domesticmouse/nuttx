# `esp32s3-korvo-2/src` Component (`boards/xtensa/esp32s3/esp32s3-korvo-2/src`)

## Overview
Board-level C implementation (`src`) for `esp32s3-korvo-2` (`xtensa/esp32s3`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 6 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[esp32s3-korvo-2.h:esp32s3_bringup]` Public declaration `esp32s3_bringup()`
- `[esp32s3-korvo-2.h:board_spiflash_init]` Public declaration `board_spiflash_init()`
- `[esp32s3-korvo-2.h:esp32s3_es8311_initialize]` Public declaration `esp32s3_es8311_initialize()`
- `[esp32s3-korvo-2.h:BUTTON_BOOT]` Hardware/board configuration macros (`BUTTON_BOOT`, `I2C_PORT`, `SPEAKER_ENABLE_GPIO`)
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
- `[esp32s3_reset.c:board_reset]` Public function `board_reset()`

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_BUTTONS`, `CONFIG_BOARDCTL_RESET`, `CONFIG_DEV_GPIO`, `CONFIG_ESP32S3_SPI`, `CONFIG_ESP32S3_TWAI`
- `[esp32s3_board_spi.c:esp32s3_spi2_status]` Validates preconditions and returns `-ENODEV` on failure
- `[esp32s3_bringup.c:esp32s3_bringup]` Validates preconditions and returns `-ENODEV` on failure
- `[esp32s3_reset.c:#error]` Compile-time guard: `CONFIG_BOARD_ASSERT_RESET_VALUE must not be equal to EXIT_SUCCESS`

## Side Effects
- `[esp32s3_board_spi.c:esp32s3_spi2_status]` Configures or drives hardware GPIO pins
- `[esp32s3_bringup.c:esp32s3_bringup]` Configures or drives hardware GPIO pins
- `[esp32s3_bringup.c:esp32s3_bringup]` Initializes/registers kernel devices or filesystems (`board_capture_initialize()`, `board_i2sdev_initialize()`, `board_sdmmc_initialize()`, `board_spidev_initialize()`, `btn_lower_initialize()`)
- `[esp32s3_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh esp32s3-korvo-2:nsh && make`
