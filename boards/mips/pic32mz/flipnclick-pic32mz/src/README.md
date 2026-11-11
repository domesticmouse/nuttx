# `flipnclick-pic32mz/src` Component (`boards/mips/pic32mz/flipnclick-pic32mz/src`)

## Overview
Board-level C implementation (`src`) for `flipnclick-pic32mz` (`mips/pic32mz`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 8 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[flipnclick-pic32mz.h:pic32mz_spidev_initialize]` Public declaration `pic32mz_spidev_initialize()`
- `[flipnclick-pic32mz.h:pic32mz_led_initialize]` Public declaration `pic32mz_led_initialize()`
- `[flipnclick-pic32mz.h:pic32mz_bringup]` Public declaration `pic32mz_bringup()`
- `[flipnclick-pic32mz.h:pic32mz_graphics_setup]` Public declaration `pic32mz_graphics_setup()`
- `[flipnclick-pic32mz.h:HAVE_SSD1306]` Hardware/board configuration macros (`HAVE_SSD1306`, `GPIO_LED_L`, `GPIO_LED_A`, `GPIO_LED_B`, `GPIO_LED_C`, `GPIO_LED_D` (+11 more))
- `[pic32mz_autoleds.c:pic32mz_led_initialize]` Public function `pic32mz_led_initialize()`
- `[pic32mz_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[pic32mz_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[pic32mz_boot.c:pic32mz_boardinitialize]` Public function `pic32mz_boardinitialize()`
- `[pic32mz_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[pic32mz_bringup.c:pic32mz_bringup]` Public function `pic32mz_bringup()`
- `[pic32mz_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[pic32mz_buttons.c:board_buttons]` Public function `board_buttons()`
- `[pic32mz_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[pic32mz_spi.c:pic32mz_spidev_initialize]` Public function `pic32mz_spidev_initialize()`
- `[pic32mz_spi.c:pic32mz_spi1select]` Public function `pic32mz_spi1select()`
- `[pic32mz_spi.c:pic32mz_spi1status]` Public function `pic32mz_spi1status()`
- `[pic32mz_spi.c:pic32mz_spi1cmddata]` Public function `pic32mz_spi1cmddata()`
- `[pic32mz_spi.c:pic32mz_spi2select]` Public function `pic32mz_spi2select()`
- `[pic32mz_spi.c:pic32mz_spi2status]` Public function `pic32mz_spi2status()`
- `[pic32mz_spi.c:pic32mz_spi2cmddata]` Public function `pic32mz_spi2cmddata()`
- `[pic32mz_spi.c:pic32mz_spi3select]` Public function `pic32mz_spi3select()`
- `[pic32mz_spi.c:pic32mz_spi3status]` Public function `pic32mz_spi3status()`
- `[pic32mz_spi.c:pic32mz_spi3cmddata]` Public function `pic32mz_spi3cmddata()`
- *(+20 additional symbols across 8 files)*

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_FLIPNCLICK_PIC32MZ_SSD1306`
- `[flipnclick-pic32mz.h:#error]` Compile-time guard: `The OLED driver requires CONFIG_PIC32MZ_SPI2 in the configuration`
- `[pic32mz_buttons.c:board_button_initialize]` Validates preconditions and returns `-ENOSYS` on failure
- `[pic32mz_spi.c:pic32mz_spidev_initialize]` Validates preconditions and returns `-ENOSYS` on failure
- `[pic32mz_ssd1306.c:#error]` Compile-time guard: `The OLED driver requires CONFIG_SPI_CMDDATA in the configuration`

## Side Effects
- `[pic32mz_autoleds.c:pic32mz_led_initialize]` Configures or drives hardware GPIO pins
- `[pic32mz_boot.c:pic32mz_boardinitialize]` Initializes/registers kernel devices or filesystems (`pic32mz_led_initialize()`, `pic32mz_spidev_initialize()`)
- `[pic32mz_bringup.c:pic32mz_bringup]` Initializes/registers kernel devices or filesystems (`nx_mount()`)
- `[pic32mz_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[pic32mz_spi.c:pic32mz_spidev_initialize]` Configures or drives hardware GPIO pins
- `[pic32mz_ssd1306.c:pic32mz_graphics_setup]` Configures or drives hardware GPIO pins
- `[pic32mz_ssd1306.c:pic32mz_graphics_setup]` Initializes/registers kernel devices or filesystems (`fb_register()`, `pic32mz_spibus_initialize()`, `ssd1306_initialize()`)
- `[pic32mz_userleds.c:board_userled_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh flipnclick-pic32mz:nsh && make`
