# `nucleo-wl55jc/src` Component (`boards/arm/stm32wl5/nucleo-wl55jc/src`)

## Overview
Board-level C implementation (`src`) for `nucleo-wl55jc` (`arm/stm32wl5`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 9 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[nucleo-wl55jc.h:board_leds_initialize]` Public declaration `board_leds_initialize()`
- `[nucleo-wl55jc.h:stm32_flash_init]` Public declaration `stm32_flash_init()`
- `[nucleo-wl55jc.h:stm32_spidev_initialize]` Public declaration `stm32_spidev_initialize()`
- `[nucleo-wl55jc.h:ipcc_init]` Public declaration `ipcc_init()`
- `[nucleo-wl55jc.h:CONFIG_SSD1680_CS_PORT]` Hardware/board configuration macros (`CONFIG_SSD1680_CS_PORT`, `CONFIG_SSD1680_DC_PORT`, `CONFIG_SSD1680_RST_PORT`, `CONFIG_SSD1680_BUSY_PORT`, `GPIO_SSD1680_CS`, `GPIO_SSD1680_CMD` (+8 more))
- `[stm32wl5_ssd1680.h:board_ssd1680_getdev]` Public declaration `board_ssd1680_getdev()`
- `[stm32_boot.c:stm32_board_initialize]` Public function `stm32_board_initialize()`
- `[stm32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[stm32_boot.c:board_ioctl]` Public function `board_ioctl()`
- `[stm32_boot.c:board_uniqueid]` Public function `board_uniqueid()`
- `[stm32_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[stm32_buttons.c:board_buttons]` Public function `board_buttons()`
- `[stm32_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[stm32_flash.c:stm32_flash_init]` Public function `stm32_flash_init()`
- `[stm32_ipcc.c:ipcc_init]` Public function `ipcc_init()`
- `[stm32_leds.c:board_leds_initialize]` Public function `board_leds_initialize()`
- `[stm32_leds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[stm32_leds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[stm32_leds.c:board_userled_initialize]` Public function `board_userled_initialize()`
- `[stm32_leds.c:board_userled]` Public function `board_userled()`
- `[stm32_leds.c:board_userled_all]` Public function `board_userled_all()`
- `[stm32_spi.c:stm32_spidev_initialize]` Public function `stm32_spidev_initialize()`
- `[stm32_spi.c:stm32_spi1select]` Public function `stm32_spi1select()`
- *(+10 additional symbols across 9 files)*

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_BOARD_FLASH_MOUNT`, `CONFIG_ARCH_BOARD_IPCC`, `CONFIG_ARCH_BUTTONS`, `CONFIG_LCD_SSD1680`, `CONFIG_SPI_DRIVER` (+1 more)
- `[stm32_boot.c:stm32_board_initialize]` Validates preconditions and returns `-EINVAL`, `-ENOTTY` on failure
- `[stm32_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure
- `[stm32_flash.c:#error]` Compile-time guard: `Sum of all flash pertitions cannot be bigger than 128`
- `[stm32_ssd1680.c:board_lcd_initialize]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[stm32_boot.c:stm32_board_initialize]` Initializes/registers kernel devices or filesystems (`board_lcd_initialize()`, `board_leds_initialize()`, `btn_lower_initialize()`, `fb_register()`, `stm32_common_initialize()`)
- `[stm32_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[stm32_flash.c:stm32_flash_init]` Initializes/registers kernel devices or filesystems (`mtdconfig_register()`, `nx_mount()`, `nxffs_initialize()`, `progmem_initialize()`, `smart_initialize()`)
- `[stm32_ipcc.c:ipcc_init]` Initializes/registers kernel devices or filesystems (`ipcc_register()`)
- `[stm32_leds.c:board_leds_initialize]` Configures or drives hardware GPIO pins
- `[stm32_spi.c:stm32_spidev_initialize]` Configures or drives hardware GPIO pins
- `[stm32_spi.c:stm32_spidev_initialize]` Initializes/registers kernel devices or filesystems (`stm32_spibus_initialize()`)
- `[stm32_ssd1680.c:board_lcd_initialize]` Configures or drives hardware GPIO pins
- `[stm32_ssd1680.c:board_lcd_initialize]` Initializes/registers kernel devices or filesystems (`ssd1680_initialize()`, `stm32_spibus_initialize()`)

## Verification
- Run: `./tools/configure.sh nucleo-wl55jc:nsh && make`
