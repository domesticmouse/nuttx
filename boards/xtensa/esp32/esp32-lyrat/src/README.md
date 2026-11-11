# `esp32-lyrat/src` Component (`boards/xtensa/esp32/esp32-lyrat/src`)

## Overview
Board-level C implementation (`src`) for `esp32-lyrat` (`xtensa/esp32`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 7 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[esp32-lyrat.h:esp32_bringup]` Public declaration `esp32_bringup()`
- `[esp32-lyrat.h:esp32_es8388_initialize]` Public declaration `esp32_es8388_initialize()`
- `[esp32-lyrat.h:board_i2sdev_initialize]` Public declaration `board_i2sdev_initialize()`
- `[esp32-lyrat.h:esp32_spiflash_init]` Public declaration `esp32_spiflash_init()`
- `[esp32-lyrat.h:esp32_gpio_init]` Public declaration `esp32_gpio_init()`
- `[esp32-lyrat.h:GPIO_LED1]` Hardware/board configuration macros (`GPIO_LED1`, `SPEAKER_ENABLE_GPIO`, `BUTTON_REC`, `BUTTON_MODE`, `BUTTON_PLAY_TP_CHANNEL`, `BUTTON_SET_TP_CHANNEL` (+8 more))
- `[esp32_boot.c:esp32_board_initialize]` Public function `esp32_board_initialize()`
- `[esp32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[esp32_bringup.c:esp32_bringup]` Public function `esp32_bringup()`
- `[esp32_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[esp32_buttons.c:board_buttons]` Public function `board_buttons()`
- `[esp32_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[esp32_gpio.c:esp32_gpio_init]` Public function `esp32_gpio_init()`
- `[esp32_reset.c:board_reset]` Public function `board_reset()`
- `[esp32_userleds.c:board_userled_initialize]` Public function `board_userled_initialize()`
- `[esp32_userleds.c:board_userled]` Public function `board_userled()`
- `[esp32_userleds.c:board_userled_all]` Public function `board_userled_all()`

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_BUTTONS`, `CONFIG_BOARDCTL_RESET`, `CONFIG_DEV_GPIO`, `CONFIG_USERLED`
- `[esp32_buttons.c:DEBUGASSERT]` Requires `id < nitems(g_buttons)`
- `[esp32_gpio.c:DEBUGASSERT]` Requires `esp32gpio != NULL && value != NULL`
- `[esp32_gpio.c:DEBUGASSERT]` Requires `esp32gpio->id < BOARD_NGPIOOUT`
- `[esp32_gpio.c:DEBUGASSERT]` Requires `esp32gpio != NULL`
- `[esp32_gpio.c:#error]` Compile-time guard: `NGPIOINT is > 0 and GPIO interrupts aren't enabled`

## Side Effects
- `[esp32_boot.c:esp32_board_initialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`)
- `[esp32_bringup.c:esp32_bringup]` Configures or drives hardware GPIO pins
- `[esp32_bringup.c:esp32_bringup]` Initializes/registers kernel devices or filesystems (`board_bmp180_initialize()`, `board_i2sdev_initialize()`, `board_lcd_initialize()`, `board_sdmmc_initialize()`, `btn_lower_initialize()`)
- `[esp32_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[esp32_gpio.c:esp32_gpio_init]` Configures or drives hardware GPIO pins
- `[esp32_gpio.c:esp32_gpio_init]` Initializes/registers kernel devices or filesystems (`gpio_pin_register()`)
- `[esp32_userleds.c:board_userled_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh esp32-lyrat:nsh && make`
