# `flipnclick-sam3x/src` Component (`boards/arm/sam34/flipnclick-sam3x/src`)

## Overview
Board-level C implementation (`src`) for `flipnclick-sam3x` (`arm/sam34`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 7 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[flipnclick-sam3x.h:sam_bringup]` Public declaration `sam_bringup()`
- `[flipnclick-sam3x.h:sam_graphics_setup]` Public declaration `sam_graphics_setup()`
- `[flipnclick-sam3x.h:HAVE_SSD1306]` Hardware/board configuration macros (`HAVE_SSD1306`, `GPIO_LED_L`, `GPIO_LED_A`, `GPIO_LED_B`, `GPIO_LED_C`, `GPIO_LED_D` (+13 more))
- `[sam_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[sam_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[sam_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[sam_boot.c:sam_boardinitialize]` Public function `sam_boardinitialize()`
- `[sam_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[sam_bringup.c:sam_bringup]` Public function `sam_bringup()`
- `[sam_spi0.c:sam_spidev_initialize]` Public function `sam_spidev_initialize()`
- `[sam_spi0.c:sam_spi0select]` Public function `sam_spi0select()`
- `[sam_spi0.c:sam_spi0status]` Public function `sam_spi0status()`
- `[sam_spi0.c:sam_spi0cmddata]` Public function `sam_spi0cmddata()`
- `[sam_ssd1306.c:sam_graphics_setup]` Public function `sam_graphics_setup()`
- `[sam_ssd1306.c:board_graphics_setup]` Public function `board_graphics_setup()`
- `[sam_userleds.c:board_userled_initialize]` Public function `board_userled_initialize()`
- `[sam_userleds.c:board_userled]` Public function `board_userled()`
- `[sam_userleds.c:board_userled_all]` Public function `board_userled_all()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_LEDS`, `CONFIG_FLIPNCLICK_SAM3X_SSD1306`, `CONFIG_SAM34_SPI0`
- `[flipnclick-sam3x.h:#error]` Compile-time guard: `The OLED driver requires CONFIG_SAM34_SPI0 in the configuration`
- `[sam_ssd1306.c:#error]` Compile-time guard: `The OLED driver requires CONFIG_SPI_CMDDATA in the configuration`

## Side Effects
- `[sam_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[sam_boot.c:sam_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`)
- `[sam_bringup.c:sam_bringup]` Initializes/registers kernel devices or filesystems (`nx_mount()`)
- `[sam_spi0.c:sam_spidev_initialize]` Configures or drives hardware GPIO pins
- `[sam_ssd1306.c:sam_graphics_setup]` Configures or drives hardware GPIO pins
- `[sam_ssd1306.c:sam_graphics_setup]` Initializes/registers kernel devices or filesystems (`fb_register()`, `sam_spibus_initialize()`, `ssd1306_initialize()`)
- `[sam_userleds.c:board_userled_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh flipnclick-sam3x:nsh && make`
